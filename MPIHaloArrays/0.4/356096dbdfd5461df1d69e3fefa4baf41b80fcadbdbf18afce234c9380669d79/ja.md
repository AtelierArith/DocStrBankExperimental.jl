```
global_domain_indices(A::MPIHaloArray)
```

`A`のドメイン領域の配列インデックスを取得します（すなわち、ハロ領域を除外）。返されるインデックスの順序は(ilo, ihi, jlo, jhi, ...)です。

# 戻り値

  * `NTuple{Int, 2 * NDimensions}` : 各次元のloおよびhiインデックスのタプル
