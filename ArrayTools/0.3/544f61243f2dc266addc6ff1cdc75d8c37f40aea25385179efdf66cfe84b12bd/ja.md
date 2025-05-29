```
cartesian_indices(A)
cartesian_indices((n1, n2, ...))
cartesian_indices((i1:j1, i2:j2, ...))
cartesian_indices(CartesianIndex(i1, i2, ...), CartesianIndex(j1, j2, ...))
cartesian_indices(R)
```

はすべて、次のそれぞれに対して多次元インデックス付けに適した `CartesianIndices` のインスタンスを生成します：配列 `A` のすべてのインデックス、次元が `(n1,n2,...)` の多次元配列、最初と最後のインデックスが `(i1,i2,...)` と `(j1,j2,...)` である多次元領域、または `R` によって定義されたカーテシアン領域、`CartesianIndices` のインスタンス。
