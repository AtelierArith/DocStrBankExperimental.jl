```
AbstractRandomShuffle <: AbstractShuffle
```

Supertype for partly or fully random shuffle algorithms such as [`RandomShuffle`](@ref) and [`GilbertShannonReeds`](@ref).

# Implementation

New random shuffling algorithms should implement either [`shuffle`](@ref) or [`shuffle!`](@ref), as appropriate. The new shuffle method should take a [`Random.AbstractRNG`](https://docs.julialang.org/en/v1/stdlib/Random/#Random.AbstractRNG) as the first argument, a collection to be shuffled as the second argument and an instance of the new shuffling algorithm type as the third argument.

For example:

```julia
struct MyShuffle <: AbstractRandomShuffle end

function shuffle!(r::AbstractRNG, c, s::MyShuffle)
    # Do the shuffling, passing r to any random number generating functions

    return c
end
```

See also: [`AbstractShuffle`](@ref)
