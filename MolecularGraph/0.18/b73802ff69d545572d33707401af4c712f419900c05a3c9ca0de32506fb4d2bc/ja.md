```
total_hydrogens(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1番目から$n$番目の原子に接続されている全水素（暗黙的および明示的）の数を表すサイズ$n$のベクターを返します。

このプロパティはSMARTS `H`クエリに対応します。
