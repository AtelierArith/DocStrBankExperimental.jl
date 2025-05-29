```
valence(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1から$n$番目の原子の内因的価数を表すサイズ$n$のベクトルを返します。

暗黙の水素の数は価数に基づいて計算されます。過剰価の原子または非有機原子の価数は、その`apparent_valence`と同じです。このプロパティはSMARTS `v`クエリに対応します。
