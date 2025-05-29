```
terms_needed(dim, stepsize, eps, alg, norm)
```

Returns the number of terms in the approximating sum that is needed to ensure an error in the given norm of at most `eps`. This depends on the dimension of the Wiener process `dim`, the current stepsize and the chosen algorithm.

See also: [`AbstractIteratedIntegralAlgorithm`](@ref), [`AbstractErrorNorm`](@ref)

# Examples

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> terms_needed(10, h, h^(3/2), Milstein(), MaxL2())
7
```

# Implementation

New algorithms should only have to implement [`errcoeff`](@ref) and [`convorder`](@ref).
