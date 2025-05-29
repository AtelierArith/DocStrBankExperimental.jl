`MyLinOp(domainType::Type, dim_in::Tuple, [domainType::Type,] dim_out::Tuple, Fwd!::Function, Adj!::Function)`

Construct a user defined `LinearOperator` by specifing its linear mapping `Fwd!` and its adjoint `Adj!`. The functions `Fwd!` and `Adj` must be in-place functions consistent with the given dimensions `dim_in` and `dim_out` and the domain and codomain types.

```julia
julia> n,m = 5,4;

julia> A = randn(n,m);

julia> op = MyLinOp(Float64, (m,),(n,), (y,x) -> mul!(y,A,x), (y,x) -> mul!(y,A',x))
A  ℝ^4 -> ℝ^5

julia> op = MyLinOp(Float64, (m,), Float64, (n,), (y,x) -> mul!(y,A,x), (y,x) -> mul!(y,A',x))
A  ℝ^4 -> ℝ^5

```
