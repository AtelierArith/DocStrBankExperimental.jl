```
get_rhs_data(ch::ConstraintHandler, A::SparseMatrixCSC) -> RHSData
```

必要な[`RHSData`](@ref)を[`apply_rhs!`](@ref)のために返します。

これは、異なる非同次ディリクレ境界条件でタイムステッピングを行う際に、同じ剛性行列が複数のステップで再利用される場合に使用する必要があります。
