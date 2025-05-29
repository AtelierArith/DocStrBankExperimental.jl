```
abstract type AbstractIteratedIntegralAlgorithm end
```

Abstract type for algorithms for the simulation of iterated integrals.

```jldoctest; setup=:(using InteractiveUtils; using LevyArea)
julia> subtypes(AbstractIteratedIntegralAlgorithm)
4-element Vector{Any}:
 Fourier
 Milstein
 MronRoe
 Wiktorsson
```
