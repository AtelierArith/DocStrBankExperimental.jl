```julia
abstract type Distance{T}
```

Distance between two [`Sequence`](@ref)s.

# Implementation

The only required method for a distance `D<:Distance` to be usable for tree contruction is

```
distance(::D{T}, ::Sequence, ::Sequence) where T
```

It is also useful to implement a default constructor. For example, if `D` is a discrete distance,

```
D() = D{Int}()
```
