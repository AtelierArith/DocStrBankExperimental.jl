```julia
σ1(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing, 
    sd::Realo=nothing)
```

Return `x` equalized (unit standard deviation).

If `sd` is provided, return `x` equalized with respect to it,

otherwise call [`σ`](@ref) with optional arguments `corrected`, `centered` and `mean` and equalize `x`.

*Examples*

```julia
using PermutationTests
x=randn(3)
μx=μ(x) # mean
σx=σ(x) # sd
xμ0=μ0(x) # centered data

# in decreasing order of efficiency
e1=σ1(xμ0; sd=σx, centered=true)
e2=σ1(xμ0; centered=true)
e3=σ1(x; mean=μx, sd=σx)
e4=σ1(x; mean=μx)

println(σ(e4)≈1.0 ? "OK" : "Error") # -> "OK"
```
