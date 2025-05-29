```
connectivity(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1から$n$番目の原子に接続されている全原子（暗黙的および明示的）の数を表すサイズ$n$のベクトルを返します。

このプロパティはSMARTS `X`クエリに対応します。
