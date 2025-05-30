```julia
addblock_matmul!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv},
    cscmatB::SparseArrays.SparseMatrixCSC{Tv, Ti},
    cscmatC::SparseArrays.SparseMatrixCSC{Tv, Ti};
    factor,
    transposed
)

```

行列の積 B と C を FEMatrixBlock A に追加します。
