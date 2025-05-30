```
create_simplicial_rectangle(nx::Int, ny::Int; p::Int=2)
```

平面上の長方形を覆う単体複体を作成します。複体は `p=0` の場合は有理数上に、`p>0` の場合は `GF(p)` 上にあります。

長方形は平面の部分集合 `[0,nx] x [0,ny]` によって与えられます。各単位正方形は、正方形の中心点で交わる4つの三角形によって表されます。ラベルの意味は次のとおりです：

  * ラベル `XXXYYYb` は点 `(XXX, YYY)` に対応します。
  * ラベル `XXXYYYc` は `(XXX + 1/2, YYY + 1/2)` に対応します。

`XXX` と `YYY` の文字数は、`nx` と `ny` の大きい方の数字の桁数に一致します。この関数は次のオブジェクトを返します：

  * 単体複体 `sc::LefschetzComplex`。
  * 頂点座標のベクトル `coords::Vector{Vector{Float64}}`。
