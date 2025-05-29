```
heavy_atoms(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1番目からn番目の原子に接続されている水素以外の原子の数を表すサイズ$n$のベクトルを返します。
