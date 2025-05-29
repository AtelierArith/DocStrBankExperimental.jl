```
which_ring(mol::SimpleMolGraph) -> Vector{Vector{Int}}
```

与えられたグラフの1から$n$番目のノードの[`sssr`](@ref)メンバーシップを表すサイズ$n$のベクターを返します。

SSSRメンバーシップは、各リングに割り当てられたSSSRインデックスのベクターとして表されます。これは、同じSSSRインデックスを持つノードが同じSSSRに属することを意味します。
