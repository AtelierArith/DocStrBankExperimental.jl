```
d_cart = project_CartData(d_cart::CartData, d::GeoData, p::ProjectionPoint)
```

GeoData構造体`d`からCartData構造体`d_cart`に、投影点`p`を中心にすべてのデータフィールドを投影します。`d_cart`は*必ず*直交カートesianグリッドでなければなりません（変形されたものは機能しません；その場合は`convert2CartData(d, proj)`を使用してください。ここで`proj`は投影点です）。

# 注意:

  * `d_cart`と`d`が水平面（3次元のサイズが1）である場合、深さ座標も補間されます。
