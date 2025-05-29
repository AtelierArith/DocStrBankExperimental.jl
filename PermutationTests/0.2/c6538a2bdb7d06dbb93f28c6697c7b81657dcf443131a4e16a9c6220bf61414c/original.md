```julia
μ0σ1(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing, 
    sd::Realo=nothing)
```

Return `x` standardized (zero mean and unit standard deviation).

If `centered` is true, equalize `x` by calling [`σ1`](@ref) with optional arguents `corrected`, `centered` and `sd`,

otherwise standardize `x` after computing the mean, if it is not provided as `mean`, and the standard deviation, if it is not provided, calling `σ`[@ref] with optional arguments `corrected` and `centered`. 

*Examples*

```julia
using PermutationTests
x=randn(3)
μx=μ(x) # mean
σx=σ(x) # sd
xμ0=μ0(x) # centered data

# in decreasing order of efficiency
z1=μ0σ1(xμ0; sd=σx, centered=true)
z2=μ0σ1(xμ0; centered=true)
z3=μ0σ1(x; mean=μx, sd=σx)
z4=μ0σ1(x; mean=μx)
z5=μ0σ1(x; sd=σx)
z6=μ0σ1(x)

println(μ(z6)≈0. ? "OK" : "Error") # -> "Ok"
println(σ(z6)≈1. ? "OK" : "Error") # -> 'OK"
```
