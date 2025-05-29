```
KroneckerMat(mat1, mat2)
```

2つのhomalg行列mat1とmat2のクロネッカー（またはテンソル）積を返します。

```jldoctest
julia> mat1 = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> mat2 = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> KroneckerMat(mat1, mat2)
[ 2    3    4    6    6    9]
[ 4    5    8   10   12   15]
[ 6    7   12   14   18   21]
[ 8   12   10   15   12   18]
[16   20   20   25   24   30]
[24   28   30   35   36   42]

julia> KroneckerMat(mat2, mat1)
[ 2    4    6    3    6    9]
[ 8   10   12   12   15   18]
[ 4    8   12    5   10   15]
[16   20   24   20   25   30]
[ 6   12   18    7   14   21]
[24   30   36   28   35   42]

```
