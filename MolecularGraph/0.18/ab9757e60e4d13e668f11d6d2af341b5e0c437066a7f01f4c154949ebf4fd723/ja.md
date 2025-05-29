```
edge_which_ring(mol::SimpleMolGraph) -> Vector{Vector{Int}}
```

与えられた分子の1から$n$番目の結合の[`sssr`](@ref) メンバーシップを表すサイズ$n$のベクターを返します。

SSSRメンバーシップは、各リングに割り当てられたSSSRインデックスのセットとして表されます。これは、同じSSSRインデックスを持つ結合が同じSSSRに属することを意味します。
