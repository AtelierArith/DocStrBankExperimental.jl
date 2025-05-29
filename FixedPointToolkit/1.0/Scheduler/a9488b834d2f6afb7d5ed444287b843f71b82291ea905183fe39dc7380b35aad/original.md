```julia
ExponentialScheduling(alpha::Float64; iter::Int64, max_iter::Int64, rate::Float64 = 1.0) --> Float64
```

Returns an alpha value descreased exponentially with the iteration `iter` with some rate `rate`.
