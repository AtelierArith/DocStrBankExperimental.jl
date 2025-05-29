```julia
submatrix(
    A::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti},
    srows,
    scols;
    factor
) -> ExtendableSparse.ExtendableSparseMatrixCSC

```

指定された行と列の番号からサブマトリックスを生成し、ExtendableSparseMatrixを作成します。
