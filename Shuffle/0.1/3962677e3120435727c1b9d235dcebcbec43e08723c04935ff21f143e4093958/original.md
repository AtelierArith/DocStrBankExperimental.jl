```
AbstractDeterministicShuffle <: AbstractShuffle
```

Supertype for fully deterministic shuffle algorithms such as [`Faro`](@ref) and [`Cut`](@ref).

# Implementation

New deterministic shuffling algorithms should implement either [`shuffle`](@ref) or [`shuffle!`](@ref), as appropriate. The new shuffle method should take a collection to be shuffled as the first argument and an instance of the new shuffling algorithm type as the second argument.

For example:

```julia
struct MyShuffle <: AbstractDeterministicShuffle
    parameter
end

function shuffle(c::AbstractArray, s::MyShuffle, prealloc_out=similar(c))
    # Do the shuffling

    return prealloc_out
end
```

Pre-allocating the output makes it easy to also write an efficient [`nshuffle!`](@ref) function for algorithms that cannot be written in-place.

See also: [`AbstractShuffle`](@ref)
