```
struct DefaultIndexHandler{N} <: AbstractIndexHandler
    offset::Int
    perm::NTuple{N,Int}
end
```

Basic index handler that stores the state of a system with `s` species in an `s`-dimensional array. The `offset` parameter denotes the offset by which the array is indexed (defaults to 1 in Julia). The order of the species is given by the tuple `perm`.

This is the simplest index handler, but it will not be optimal if some states cannot be reached from the initial state, e.g. due to the presence of conservation laws. In these cases one should use try to remove redundant species where possible.

Constructors: `DefaultIndexHandler([sys::FSPSystem, offset::Int=1])`
