```julia
Monkhorst(ind::Int64, N::Int64) --> Float64
Monkhorst(ind::Int64, N::Int64, shift::Int64, BC::Float64) --> Float64
```

The usual Monkhorst grid is defined as follows $[\frac{2i - (N+1)}{2N}, i∈[1, N]]$ The modified Monkhorst grid takes into account the desired boundary condition `BC`, and an integer `shift` (if required, to change the starting point), and shifts the momentum grid accordingly.
