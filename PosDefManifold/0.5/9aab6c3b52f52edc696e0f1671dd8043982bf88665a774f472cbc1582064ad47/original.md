```
mean(metric::Metric, ν::Vector{T}) where T<:RealOrComplex
```

Mean of $k$ real or complex scalars, using the specified `metric`  of type [Metric::Enumerated type](@ref). Note that using the Fisher,  logEuclidean and Jeffrey metric, the resulting mean  is the scalar geometric mean. Note also that the code of this method  is in unit *statistics.jl*, while the code for all the others is  in unit *riemannianGeometry.jl*.

**Examples**

```julia
using PosDefManifold
# Generate 10 random numbers distributed as a chi-square with 2 df.
ν=[randχ²(2) for i=1:10]
arithmetic_mean=mean(Euclidean, ν)
geometric_mean=mean(Fisher, ν)
harmonic_mean=mean(invEuclidean, ν)
harmonic_mean<=geometric_mean<=arithmetic_mean # AGH inequality
```
