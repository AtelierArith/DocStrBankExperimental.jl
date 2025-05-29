```julia
SparseMatrixCSB(
    A::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer}
) -> CompressedSparseBlocks.SparseMatrixCSB{Tv, Ti} where {Tv, Ti<:Integer}
SparseMatrixCSB(
    A::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer},
    beta::Integer
) -> CompressedSparseBlocks.SparseMatrixCSB{Tv, Ti} where {Tv, Ti<:Integer}

```

`SparseMatrixCSC` 行列 `A` を `SparseMatrixCSB` 行列に変換します。

# オプション引数

  * `beta`: 各ブロックのサイズの2の対数; 0の場合、パッケージが内部でブロックサイズを決定します。
