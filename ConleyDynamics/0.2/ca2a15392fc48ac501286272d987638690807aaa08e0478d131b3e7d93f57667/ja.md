```
planar_nontransverse_edges(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf;
                           npts::Int=100)
```

平面レフシェッツ複体のすべてのエッジを見つけますが、フローが横断的でないものです。

レフシェッツ複体は `lc` で与えられ、複体のすべての頂点の座標は `coords` にあり、ベクトル場は `vf` で指定されています。オプションのパラメータ `npts` は、横断性チェックのためにエッジに沿って評価されるポイントの数を決定します。この関数は、エッジのインデックスを含む `Vector{Int}` として非横断的エッジのリストを返します。
