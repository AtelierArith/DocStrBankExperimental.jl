```
Base.@kwdef struct AlgebraicBorderSolver{
    D,
    A<:Union{Nothing,SS.AbstractGröbnerBasisAlgorithm},
    S<:Union{Nothing,SS.AbstractAlgebraicSolver},
}
    algorithm::A = nothing
    solver::S = nothing
end
```

`algorithm` と `solver` を使用して境界基底を解決するには、まずそれを `BorderBasis{D}` に変換します。
