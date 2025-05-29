```
create_simplicial_delaunay(boxw::Real, boxh::Real, npoints::Int;
                           p::Int=2)
```

ボックス内に平面デローニ三角形分割を作成します。複体は `p=0` の場合は有理数上に、`p>0` の場合は `GF(p)` 上にあります。

この関数は、長方形のボックス `[0,boxw] x [0,boxh]` 内に `npoints` 点のランダムサンプルを選択します。ランダムサンプルから、関数はデローニ三角形分割を作成し、以下のオブジェクトを返します：

  * シンプレクシャル複体 `sc::LefschetzComplex`。
  * 頂点座標のベクトル `coords::Vector{Vector{Float64}}`。

この関数は、与えられた長方形の完全な三角形分割を提供しないことに注意してください。境界付近には隙間があります。
