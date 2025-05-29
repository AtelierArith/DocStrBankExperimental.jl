```
RowProjectionMatrix{T} <: AbstractArray{T, 2}
```

Implicit matrix projecting a sequence of rows of a given matrix with elements of type `T`.

# Constructors

```
RowProjectionMatrix(base, rows)
RowProjectionMatrix(base, rows...)
RowProjectionMatrix{T}(base, rows)
```

Create a new row-projected matrix from the given `base` matrix and a list or sequence of `rows` corresponding to it. Rows can be used multiple times and in any order.

# Examples

```jldoctest; setup = :(using ImplicitArrays)
julia> M = [10 20 30; 40 50 60; 70 80 90];

julia> RowProjectionMatrix(M, [1, 3])
2×3 RowProjectionMatrix{Int64, Matrix{Int64}}:
 10  20  30
 70  80  90

julia> RowProjectionMatrix(M, 2, 3, 2)
3×3 RowProjectionMatrix{Int64, Matrix{Int64}}:
 40  50  60
 70  80  90
 40  50  60
```

!!! note
    Changing an element through `RowProjectionMatrix` actually changes the element in the underlying array. The changes are still reflected in the `RowProjectionMatrix`. Thus, caution is advised when changing elements of rows that are contained multiple times in the projection, in order to avoid unwanted side effects.

