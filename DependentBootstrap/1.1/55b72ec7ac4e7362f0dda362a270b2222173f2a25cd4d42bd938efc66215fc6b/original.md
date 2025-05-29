```
dbootlevel1(data::T1, bi::BootInput)
dbootlevel1(data::T1; kwargs...)
```

Get the level 1 bootstrapped statistics associated with dataset in data, and bootstrap methodology in BootInput.

A keyword method that calls the keyword constructor for BootInput is also provided. Please use ?BootInput at the REPL for more detail on feasible keywords.

Note, the return type is determined by bi.flevel1, which must be a function that accepts T1, ie typeof(data), as input. It may return any output type T2, as long as bi.flevel2 will accept Vector{T2} as input.

For example, if data is a Vector{<:Number} then bi.flevel1 might be the function mean, which in this case will return Float64, so bi.flevel2 must be some function that can accept Vector{Float64} as input.

A more complicated example: if data is Matrix{<:Number} then bi.flevel1 might be the anonymous function x->mean(x,dims=1), which in this case will return a single row Matrix{Float64}, and so bi.flevel2 must be some function that can accept Vector{Matrix{Float64}} as input.
