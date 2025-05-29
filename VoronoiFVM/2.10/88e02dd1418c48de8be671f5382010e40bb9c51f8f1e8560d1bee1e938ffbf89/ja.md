```julia
mass_matrix(state)

```

[`SciMLBase.ODEFunction`](@ref)と一緒に使用するための質量行列を計算します。対角行列である場合は対角行列を返し、そうでない場合はSparseMatrixCSCを返します。
