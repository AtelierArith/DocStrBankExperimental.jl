```
AlmostBlockDiagonal{T, I <: Integer, V <: AbstractMatrix{T}} <: AbstractMatrix{T}
```

対角にブロック行列がある行列ですが、厳密にはそれらのコーナーが互いに接しているわけではありません。

例えば：

10 x 10 の行列：

x  x  x  x x  x  x  x x  x  x  x       x  x  x  x       x  x  x  x             x  x  x  x             x  x  x  x                   x  x  x  x                   x  x  x  x                   x  x  x  x

は次のように抽象化できます：

```julia
julia> AlmostBlockDiagonal([rand(3,4),rand(2,4),rand(2,4),rand(3,4)], [2,2,2,4])
```

ここで、最初の引数はほぼブロック対角行列のフィラーであり、2番目の引数は対角の各隣接ブロックのオフセットです。

! 注     ブロックの列 `ncol` と行 `nrow` は次の条件を満たさなければなりません： `ncol` ≥ `nrow`。

この実装は主に論文から来ています：[SOLVEBLOK: A Package for Solving Almost Block Diagonal Linear Systems](https://dl.acm.org/doi/pdf/10.1145/355873.355880) これは、スケール行ピボッティングによるガウス消去法でほぼブロック対角系を解くための元々のFORTRANプログラムです。
