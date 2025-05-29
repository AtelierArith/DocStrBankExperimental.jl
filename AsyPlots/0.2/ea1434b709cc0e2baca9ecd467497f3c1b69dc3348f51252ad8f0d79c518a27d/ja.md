```
Surface(x::Array{<:Real},
        y::Array{<:Real},
        z::Array{<:Real,2};
        options)
Surface(z::Array{<:Real},2)
```

三次元の表面を表すグラフィックスプリミティブ `x` と `y` は、一次元または二次元の配列である可能性があります。

表面は、点 [x[i,j],y[i,j],z[i,j] for i=1:size(z,1),j=1:size(z,2)] を通過します。

オプションは次のとおりです。

  * `colors`: 色付けのための色名のベクトル
  * `spline`: 滑らかな表面または部分的に滑らかな表面を描画するかどうか
  * `surfacepen`: 表面を描画するためのペン
  * `meshpen`: 表面上のグリッド線を描画するためのペン
  * `clip`: `false` または `x`、`y`、`z` と同じ次元のブール配列で、除外するパッチを指定します
