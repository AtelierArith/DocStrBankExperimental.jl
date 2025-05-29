```
pmrand([::Type{T},] m::Vector{Int},n::Vector{Int}[, period = 10])
```

Generate a random discrete-time periodic matrix of type  `PeriodicMatrix` with period  `period` (default:  `period = 10`).  The time-varying row and column dimensions of component matrices are specified by the integer vectors `m` and `n`, respectively. `T` is the type of matrix elements, which assumes by default value `T = Float64` if omitted.
