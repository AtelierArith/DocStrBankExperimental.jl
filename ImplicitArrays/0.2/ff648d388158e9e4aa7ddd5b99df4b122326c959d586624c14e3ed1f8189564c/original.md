```
RowProjectionVector{T} <: AbstractArray{T, 1}
```

Implicit vector projecting a sequence of rows of a given vector with elements of type `T`.

# Constructors

```
RowProjectionVector(base, rows)
RowProjectionVector(base, rows...)
RowProjectionVector{T}(base, rows)
```

Create a new row-projected vector from the given `base` vector and a list or sequence of `rows` corresponding to it. Rows can be used multiple times and in any order.

# Examples

```jldoctest; setup = :(using ImplicitArrays)
julia> v = [10, 20, 30, 40, 50];

julia> RowProjectionVector(v, [1, 3, 5])
3-element RowProjectionVector{Int64, Vector{Int64}}:
 10
 30
 50

julia> RowProjectionVector(v, 2, 3, 2)
3-element RowProjectionVector{Int64, Vector{Int64}}:
 20
 30
 20
```

!!! note
    Changing an element through `RowProjectionVector` actually changes the element in the underlying array. The changes are still reflected in the `RowProjectionVector`. Thus, caution is advised when changing elements of rows that are contained multiple times in the projection, in order to avoid unwanted side effects.

