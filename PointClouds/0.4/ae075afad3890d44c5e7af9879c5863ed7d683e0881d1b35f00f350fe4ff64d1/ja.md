```
transform(p::PointCloud; crs)
```

`PointCloud`の座標を新しい座標参照系（CRS）に変換します。現在のCRSがない場合、座標は変更されず、新しいCRSが`PointCloud`に追加されます。

必要なキーワード引数`crs`は、[PROJライブラリ](https://proj.org/en/9.4/usage/quickstart.html)によって理解される任意の文字列にすることができます。`nothing`に設定すると、CRSは削除されます。
