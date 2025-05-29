```
Solver(D1, D2 = nothing, D3 = nothing)
```

Create a solver, where `D1` is an `AbstractDerivativeOperator` from [SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) of first `derivative_order`, `D2` is an `AbstractDerivativeOperator`  of second `derivative_order` or an `AbstractMatrix`, and `D3` is an `AbstractDerivativeOperator` of third `derivative_order` or an `AbstractMatrix`. `D2` and `D3` can also be `nothing` if that derivative is not used by the discretization. All given summation-by-parts operators should be associated with the same grid.
