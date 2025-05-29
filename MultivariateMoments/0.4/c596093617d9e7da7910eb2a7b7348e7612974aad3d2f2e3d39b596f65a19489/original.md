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

Solve a border basis using `algorithm` and `solver by first converting it to a`BorderBasis{D}`.
