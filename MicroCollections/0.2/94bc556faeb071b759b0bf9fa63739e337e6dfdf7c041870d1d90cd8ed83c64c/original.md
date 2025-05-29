```
singletonshim(ContainerType, x)
```

Create a "shim" container with one element `x` that is widen to `ContainerType` when appending elements to it.

# Examples

```jldoctest
julia> using MicroCollections, BangBang

julia> @assert push!!(singletonshim(BitVector, false), true)::BitArray == [false, true]
```
