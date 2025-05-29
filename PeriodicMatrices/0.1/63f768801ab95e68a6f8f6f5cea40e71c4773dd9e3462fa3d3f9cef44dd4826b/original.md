```
pmrand(::Type{PM}, n::Int, m::Int[, period = 10]; ns = 1) 
pmrand(::Type{PM{:d,T}}, n::Int, m::Int[, period = 10]; ns = 1) 
pmrand(::Type{PM}, n::Vector{Int}, m::Vector{Int}[, period = 1]) 
pmrand(SwitchingPeriodicMatrix, n, m[, period = 10]; ns = [period]) 
pmrand(SwitchingPeriodicArray, n, m[, period = 10]; ns = [period])
```

Generate a random `n×m` discrete-time periodic matrix of type `PM` or `PM{:d,T}` with period  `period` (default:  `period = 10`) with  `ns` component matrices (default: `ns = 1`).  If `PM = PeriodicMatrix` or `PM = PeriodicArray`, `ns` specifies the number of component matrices (default: `ns = 10`). If `PM = PeriodicMatrix`, then two integer vectors `n` and `m` containing the row and column dimensions of the the component matrices, respectively, can be used to specify periodic matrices with time-varying dimensions. 

If `PM = SwitchingPeriodicMatrix` or `PM = SwitchingPeriodicArray`, the integer vector `ns` specifies the switching moments (default: `ns = [period]). The type`T`of matrix elements can be specified using, e.g.`PeriodicMatrix{:d,T}`instead`PeriodicMatrix`,  which assumes by default`T = Float64`.
