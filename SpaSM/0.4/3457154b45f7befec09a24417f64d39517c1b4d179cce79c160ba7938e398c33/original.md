```
solve(fact::LU{F}, b::Vector{ZZp{F}}, x::Union{Vector{ZZp{F}},Nothing} = nothing)
```

Solve `x`*`A` == `b`, where `A` has already been echelonized as `fact`. Returns solution `x` or `nothing` if no solution
