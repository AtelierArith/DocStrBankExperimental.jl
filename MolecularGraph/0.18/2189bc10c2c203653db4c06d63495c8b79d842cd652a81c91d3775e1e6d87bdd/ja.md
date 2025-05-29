```
ring_count(mol::MolGraph) -> Vector{Int}
```

与えられた分子の1から$n$番目の原子が属する[`sssr`](@ref)の数を表すサイズ$n$のベクトルを返します。

このプロパティはSMARTS `R`クエリに対応します。
