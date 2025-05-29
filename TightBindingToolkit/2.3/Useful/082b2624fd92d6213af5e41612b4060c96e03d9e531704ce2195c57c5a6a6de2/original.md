```julia
BinarySearch(target::Float64, xRange::Tuple{Float64, Float64}, f::T, args::Tuple ; tol::Float64=0.001)
```

General function implementing Binary search on a monotonic function f(x, args...)=target, in the range x ∈ xRange, with tolerance tol. 
