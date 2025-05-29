`Zeros(domainType::Type, dim_in::Tuple, [codomainType::Type,] dim_out::Tuple)`

Create a `LinearOperator` which, when multiplied with an array `x` of size `dim_in`, returns an array `y` of size `dim_out` filled with zeros.

For convenience `Zeros` can be constructed from any `AbstractOperator`.

```julia
julia> Zeros(Eye(10,20))
0  ℝ^(10, 20) -> ℝ^(10, 20)

julia> Zeros([Eye(10,20) Eye(10,20)])
[0,0]  ℝ^(10, 20)  ℝ^(10, 20) -> ℝ^(10, 20)
```
