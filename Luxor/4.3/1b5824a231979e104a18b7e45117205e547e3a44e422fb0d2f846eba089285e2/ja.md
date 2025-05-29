```
rule(pos, theta;
    boundingbox=BoundingBox(),
    vertices=false)
```

`pos`を通り、x軸から角度`theta`で直線を描きます。

デフォルトでは、線は描画全体にわたりますが、BoundingBoxを指定することで線の範囲を変更できます。

```julia
rule(O)       # x軸を描画
rule(O, pi/2) # y軸を描画
```

関数：

```julia
rule(O, pi/2, boundingbox=BoundingBox()/2)
```

は、描画の幅と高さの半分の範囲を持つバウンディングボックスにわたる線を描きます。

2つの端点をベクトルで返します。

`vertices=true`を使用すると、線を描画せずに端点のみを返します。
