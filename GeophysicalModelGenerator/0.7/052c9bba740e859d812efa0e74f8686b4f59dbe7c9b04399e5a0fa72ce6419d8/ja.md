```
d_cart = project_CartData(d_cart::CartData, d::UTMData, p::ProjectionPoint)
```

UTMData構造体`d`のすべてのデータフィールドを、投影点`p`の周りでCartData構造体`d_cart`に投影します。 `d_cart`は*必ず*直交カルテシアングリッドでなければなりません（変形は機能しません; その場合は`convert2CartData(d, proj)`を使用してください。`proj`は投影点です）。

```
# 注意:    
- `d_cart`と`d`が水平面（3次元のサイズ==1）である場合、深さ座標も補間します。
```
