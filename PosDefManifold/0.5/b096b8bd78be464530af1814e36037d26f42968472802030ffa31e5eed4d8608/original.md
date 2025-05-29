```
std(metric::Metric, ν::Vector{T};
    corrected::Bool=true,
    mean=nothing) where T<:RealOrComplex
```

Standard deviation of $k$ real or complex scalars,  using the specified `metric`  of type [Metric::Enumerated type](@ref) and the  specified `mean` if provided.

Only the Euclidean and Fisher  metric are supported by this function. Using the Euclidean  metric return the output of standard Julia  [std](https://docs.julialang.org/en/v1/stdlib/Statistics/#Statistics.std)  function. Using the Fisher metric return the scalar geometric standard deviation,  which is defined such as,

$\sigma=\text{exp}\Big(\sqrt{k^{-1}\sum_{i=1}^{k}\text{ln}^2(v_i/\mu})\Big)$.

If `corrected` is `true`, then the sum is scaled with $k-1$,  whereas if it is `false` the sum is scaled with $k$.

**Examples**

```julia
using PosDefManifold
# Generate 10 random numbers distributed as a chi-square with 2 df.
ν=[randχ²(2) for i=1:10]
arithmetic_sd=std(Euclidean, ν) # mean not provided
geometric_mean=mean(Fisher, ν)
geometric_sd=std(Fisher, ν, mean=geometric_mean) # mean provided
```
