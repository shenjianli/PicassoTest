## Picasso使用实例 ##

###实现的例子效果图如下：###

![picasso](/img/Picasso_test.png) 
图片右上角红色三角表示这张图片是从网络上下载显示出来的，绿色三角表示是从内存缓存中加载的图片


![picasso test](/img/Picasso_test1.png)
这张效果图中的黄色三角表示图片是从本地缓存中读取出来的


###这个例子的工程结构图如下：###
![picasso struct](/img/Picasso_struct_pic.jpg)

主布局文件
```
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="${relativePackage}.${activityClass}" >
    <ListView
        android:id="@+id/listview"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        android:dividerHeight="1dip" />
</RelativeLayout>
```
这个布局文件就是全屏显示一个列表ListView视图控件，没有什么要说的！

ListView中Item布局如下：
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:layout_gravity="center_vertical"
    android:padding="5dip" >

    <ImageView
        android:id="@+id/imageView1"
        android:layout_width="60dip"
        android:layout_height="60dip"
        android:src="@drawable/ic_launcher" />

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:layout_marginLeft="15dip"
         >

        <TextView
            android:id="@+id/textView1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="TextView" 
            android:textSize="20sp"
            android:layout_marginTop="5dip"/>

        <TextView
            android:id="@+id/textView2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="TextView" 
            android:textSize="14sp"
            android:layout_marginTop="2dip"/>
    </LinearLayout>

</LinearLayout>
```
这个布局文件是用来设置ListView中每项需要显示的控件，左边ImageView显示一张图片，右边坚排两个TextView来显示两段文字！


MainActivity和Listview适配器代码如下：

```

package com.shen.picasso;

import java.util.ArrayList;

import android.app.Activity;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.ImageView;
import android.widget.ListView;
import android.widget.TextView;

import com.squareup.picasso.Picasso;

public class MainActivity extends Activity {
	//设置图片请求的基础地址
	private static final String BASE_URL = "http://img1.3lian.com/img2011/w1/106/85/";
	
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		//创建一组数据用来填充ListView时在界面显示数据
		ArrayList<Product> dishList = new ArrayList<Product>();
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		dishList.add(new Product(BASE_URL + "42.jpg", "水煮鱼片", "38.00"));
		dishList.add(new Product(BASE_URL + "34.jpg", "小炒肉", "18.00"));
		dishList.add(new Product(BASE_URL + "37.jpg", "清炒时蔬", "15.00"));
		dishList.add(new Product(BASE_URL + "11.jpg", "金牌烤鸭", "36.00"));
		dishList.add(new Product(BASE_URL + "12.jpg", "粉丝肉煲", "20.00"));
		
		//获取ListView组件并设置数据适配器
		ListView mListView = (ListView) this.findViewById(R.id.listview);
		ProductListViewAdapter adapter = new ProductListViewAdapter(dishList);
		mListView.setAdapter(adapter);
	}

	// ListView适配器
	private class ProductListViewAdapter extends BaseAdapter {

		private ArrayList<Product> dataList;

		public ProductListViewAdapter(ArrayList<Product> list) {
			this.dataList = list;
		}

		@Override
		public int getCount() {
			return dataList.size();
		}

		@Override
		public Object getItem(int position) {
			return dataList.get(position);
		}

		@Override
		public long getItemId(int position) {
			return position;
		}

		@Override
		public View getView(int position, View convertView, ViewGroup parent) {
			ListViewItemHolder item = null;
			//加载ListView中每项的布局文件
			if (convertView == null) {
				convertView = LayoutInflater.from(MainActivity.this).inflate(
						R.layout.product_listview_item, null);
				item = new ListViewItemHolder();
				item.imgIv = (ImageView) convertView
						.findViewById(R.id.imageView1);
				item.nameTv = (TextView) convertView
						.findViewById(R.id.textView1);
				item.priceTv = (TextView) convertView
						.findViewById(R.id.textView2);

				convertView.setTag(item);
			} else {
				item = (ListViewItemHolder) convertView.getTag();
			}

			Product product = dataList.get(position);

			//设置是否在图片右上角显示三角形来说明图片来源（网络，本地，内存）
			Picasso.with(MainActivity.this).setIndicatorsEnabled(true);
			
			//这里就是异步加载网络图片的地方
			Picasso.with(MainActivity.this).load(product.getImgUrl()).transform(new CircleTransform())
					.into(item.imgIv);

			item.nameTv.setText(product.getName());
			item.priceTv.setText(product.getPrice() + "元");

			return convertView;
		}

	}

	// ListView的Item组件类
	private class ListViewItemHolder {
		ImageView imgIv;
		TextView nameTv;
		TextView priceTv;
	}
}

```

上面代码过长，我就不一一说明了，并且代码中关键点我也写了注释，想了解的可以看一下，在这里我重点说一下源码中 Picasso.with(MainActivity.this).setIndicatorsEnabled(true);这句代码，这句代码是用来在图片右上角来显示标志一个三角标志的，有人会问这个标志有什么用途了？这个标志充分体验上Google程序员高大上的地方（代码给使用者良好的体验），这里的标志用来说明图片是从网络，本地，或是内存中加载出来的，形象的来说明图片的缓存机制！红色三角表示从网络上下载显示的，黄色三角表求图片是从本地文件硬盘读取的，若三色为绿色表求图片是直接从内存缓存中加载的，这也更加形象的说明了Picasso的三级图片缓存机制！ 

注：这个三角标志可以从上面的效果图片中清晰的看出来


细心的读者可能发现上面Picasso.with(MainActivity.this).load(product.getImgUrl()).transform(new CircleTransform()).into(item.imgIv);代码调用了transform(new CircleTransform())这个方法，这个在这里起什么作用了？Picasso这个库支持进行图片变换，这里的作用就是把图片变换成圆形显示！

进行图片变换为圆形的转换器代码如下：
```
package com.shen.picasso;

import android.graphics.Bitmap;
import android.graphics.BitmapShader;
import android.graphics.Canvas;
import android.graphics.Paint;

import com.squareup.picasso.Transformation;

public class CircleTransform implements Transformation {
	@Override
	public Bitmap transform(Bitmap source) {
		int size = Math.min(source.getWidth(), source.getHeight());

		int x = (source.getWidth() - size) / 2;
		int y = (source.getHeight() - size) / 2;

		Bitmap squaredBitmap = Bitmap.createBitmap(source, x, y, size, size);
		if (squaredBitmap != source) {
			source.recycle();
		}

		Bitmap bitmap = Bitmap.createBitmap(size, size, source.getConfig());

		Canvas canvas = new Canvas(bitmap);
		Paint paint = new Paint();
		BitmapShader shader = new BitmapShader(squaredBitmap,
				BitmapShader.TileMode.CLAMP, BitmapShader.TileMode.CLAMP);
		paint.setShader(shader);
		paint.setAntiAlias(true);

		float r = size / 2f;
		canvas.drawCircle(r, r, r, paint);

		squaredBitmap.recycle();
		return bitmap;
	}

	@Override
	public String key() {
		return "circle";
	}
}
```

Listview中填充的数据对象类如下：
```
package com.shen.picasso;

//表示菜类（经过烹调的蔬菜、蛋品、肉类等）
public class Product {

	private String imgUrl; // 图片地址
	private String name; // 菜名
	private String price; // 菜价
	
	public Product(String imgUrl, String name, String price) {
		this.imgUrl = imgUrl;
		this.name = name;
		this.price = price;
	}

	public String getImgUrl() {
		return imgUrl;
	}

	public void setImgUrl(String imgUrl) {
		this.imgUrl = imgUrl;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getPrice() {
		return price;
	}

	public void setPrice(String price) {
		this.price = price;
	}

}

```
			