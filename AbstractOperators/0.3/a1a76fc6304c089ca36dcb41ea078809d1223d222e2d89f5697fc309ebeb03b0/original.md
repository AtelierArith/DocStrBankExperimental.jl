`MatrixOp(domainType=Float64::Type, dim_in::Tuple, A::AbstractMatrix)`

`MatrixOp(A::AbstractMatrix)`

`MatrixOp(A::AbstractMatrix, n_colons)`

Creates a `LinearOperator` which, when multiplied with a vector `x::AbstractVector`, returns the product `A*x`.

The input `x` can be also a matrix: the number of columns must be given either in the second entry of `dim_in::Tuple` or using the constructor `MatrixOp(A::AbstractMatrix, n_colons)`.

```julia
julia> MatrixOp(Float64,(10,),randn(20,10))
▒  ℝ^10 -> ℝ^20 

julia> MatrixOp(randn(20,10))
▒  ℝ^10 -> ℝ^20

julia> MatrixOp(Float64,(10,20),randn(20,10))
▒  ℝ^(10, 20) -> ℝ^(20, 20)

julia> MatrixOp(randn(20,10),4)
▒  ℝ^(10, 4) -> ℝ^(20, 4)

```
