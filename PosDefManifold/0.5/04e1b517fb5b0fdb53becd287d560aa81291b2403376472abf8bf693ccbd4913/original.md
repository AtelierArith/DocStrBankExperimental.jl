```julia
    (1) means(metric::Metric, 𝒫::ℍVector₂;
    <⏩=true>)

    (2) means(metric::Metric, 𝒟::𝔻Vector₂;
    <⏩=true>)
```

(1) Given a 2d array $𝒫$ of positive definite matrices as an [ℍVector₂ type](@ref) compute the [Fréchet mean](@ref) for as many [ℍVector type](@ref) objects as hold in $𝒫$, using the specified `metric` of type [Metric::Enumerated type](@ref). Return the means in a vector of `Hermitian` matrices, that is, as an `ℍVector` type.

(2) Given a 2d array $𝒟$ of real positive definite matrices as an [𝔻Vector₂ type](@ref) compute the [Fréchet mean](@ref) for as many [𝔻Vector type](@ref) objects as hold in $𝒟$, using the specified `metric` of type [Metric::Enumerated type](@ref). Return the means in a vector of `Diagonal` matrices, that is, as a `𝔻Vector` type.

The weigted Fréchet mean is not supported in this function.

If `⏩=true` (default) the computation of the means is multi-threaded.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


**See also**: [`mean`](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)
# Generate a set of 40 random 4x4 SPD matrices
Qset=randP(3, 40) # or, using unicode: 𝐐=randP(3, 40)
# listing directly ℍVector objects
means(logEuclidean, ℍVector₂([Pset, Qset])) # or: means(logEuclidean, ℍVector₂([𝐏, 𝐐]))
# note that [𝐏, 𝐐] is actually a ℍVector₂ type object

# creating and passing an object of ℍVector₂ type
sets=ℍVector₂(undef, 2) # or: 𝒫=ℍVector₂(undef, 2)
sets[1]=Pset # or: 𝒫[1]=𝐏
sets[2]=Qset # or: 𝒫[2]=𝐐
means(logEuclidean, sets) # or: means(logEuclidean, 𝒫)

# going multi-threated

# first, create 20 sets of 200 50x50 SPD matrices
sets=ℍVector₂([randP(50, 200) for i=1:20])

# How much computing time we save ?
# (example min time obtained with 4 threads & 4 BLAS threads)
using BenchmarkTools

# non multi-threaded, mean with closed-form solution
@benchmark(means(logEuclidean, sets; ⏩=false)) # (6.196 s)

# multi-threaded, mean with closed-form solution
@benchmark(means(logEuclidean, sets)) # (1.897 s)

sets=ℍVector₂([randP(10, 200) for i=1:10])

# non multi-threaded, mean with iterative solution
# wait a bit
@benchmark(means(Fisher, sets; ⏩=false)) # (4.672 s )

# multi-threaded, mean with iterative solution
@benchmark(means(Fisher, sets)) # (1.510 s)
```
