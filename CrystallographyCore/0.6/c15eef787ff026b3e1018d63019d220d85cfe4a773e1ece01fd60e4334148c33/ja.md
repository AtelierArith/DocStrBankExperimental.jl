```
Cell(lattice, positions, atoms)
```

新しいセルを作成します。

引数 `lattice` は [`Lattice`](@ref) 型です。分数原子位置 `positions` は、$N$ 個の浮動小数点値を持つベクトルのベクトルによって与えられ、$N$ は原子の数です。引数 `atoms` は $N$ 個の値のリストであり、同じ種類の原子は同じタイプである必要があります。
