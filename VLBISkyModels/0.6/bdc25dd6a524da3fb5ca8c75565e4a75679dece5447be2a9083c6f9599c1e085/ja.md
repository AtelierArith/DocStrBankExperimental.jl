```
MRing(c::Union{NTuple{N, <:Complex}, AbstractVector{<:Complex}})
```

複素ベクトル `c` から MRing 幾何モデルを構築します。このベクトルはフーリエ展開の実数および虚数（またはコサインとサイン）係数に対応します。型の `N` はフーリエ展開の次数を定義します。
