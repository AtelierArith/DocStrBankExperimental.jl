The `ConvergenceTest` abstract type represents mechanisms to decide when the iteration has converged.

```
converged(ct::ConvergenceTest, meas::Vector{KRatio}, computed::Dict{Element,<:AbstractFloat})::Bool
```
