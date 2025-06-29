```
create_cubical_rectangle(nx::Int, ny::Int;
                         p::Int=2, randomize::Real=0.0)
```

平面上の長方形を覆う立方体複体を作成します。複体は `p=0` の場合は有理数の上にあり、`p>0` の場合は `GF(p)` の上にあります。

長方形は平面の部分集合 `[0,nx] x [0,ny]` によって与えられ、各単位正方形は結果として得られる立方体複体の中で二次元の立方体を提供します。この関数は以下のオブジェクトを返します：

  * 立方体複体 `cc::LefschetzComplex`
  * 頂点座標のベクトル `coords::Vector{Vector{Float64}}`

オプションのパラメータ `randomize` に正の実数の分数 `r` が0.5未満で割り当てられた場合、実際の座標はランダム化されます。これらは各頂点を中心とした半径 `r` の円盤から一様に選ばれます。
