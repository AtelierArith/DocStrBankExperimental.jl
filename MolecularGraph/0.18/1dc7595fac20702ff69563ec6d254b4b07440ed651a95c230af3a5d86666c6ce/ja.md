```
smallest_ring(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1から$n$番目の原子が属する最小の [`sssr`](@ref) のサイズを表すサイズ$n$のベクターを返します。

ノードがリングに属していない場合、その値は0になります。このプロパティはSMARTS `r` クエリに対応します。
