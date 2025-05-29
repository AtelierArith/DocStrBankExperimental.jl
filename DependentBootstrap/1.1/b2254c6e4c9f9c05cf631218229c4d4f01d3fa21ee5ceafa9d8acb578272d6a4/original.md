```
dboot(data, bi::BootInput)
dboot(data ; kwargs...)
```

Get the level 2 bootstrapped statistics associated with dataset in data, and bootstrap methodology in BootInput.

A keyword method that calls the keyword constructor for BootInput is also provided. Please use ?BootInput at the REPL for more detail on feasible keywords.

Note, the return type of the output will be determined by bi.flevel2, which must be a function that accepts Vector{T}, where T is the output type of bi.flevel1.

For example, if data is a Vector{<:Number} and bi.flevel1 is mean, then in this case, bi.flevel1 will return Float64, and so bi.flevel2 must be some function that accepts Vector{Float64} as input (and can have any output type.)

Alternatively, bi.flevel2 could be the anonymous function (x -> quantile(x, [0.025, 0.975])), in which case the input should be Vector{Float64}, and so bi.flevel1 should return Float64. Note, the output of bi.flevel2 in this case will be a 2-element Vector{Float64} with elements corresponding bootstrapped 95% confidence interval for the level1 statistic of the input dataset
