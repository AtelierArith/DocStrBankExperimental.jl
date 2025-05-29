```
BoxDiagDirections{N, VN} <: AbstractDirections{N, VN}
```

Box-diagonal directions representation.

### Fields

  * `n` – dimension

### Notes

Box-diagonal directions can be seen as the union of diagonal directions (all entries are ±1) and box directions (one entry is ±1, all other entries are 0). The iterator first enumerates all diagonal directions and then all box directions. In dimension $n$, there are in total $2^n + 2n$ such directions (exception: for $n = 1$, there are $2$ directions).

## Examples

The template can be constructed by passing the dimension. For example, in two dimensions:

```jldoctest dirs_BoxDiag
julia> dirs = BoxDiagDirections(2)
BoxDiagDirections{Float64, Vector{Float64}}(2)

julia> length(dirs) # number of directions
8
```

By default, each direction is represented as a regular vector:

```jldoctest dirs_BoxDiag
julia> eltype(dirs)
Vector{Float64} (alias for Array{Float64, 1})
```

In two dimensions, the directions are normal to the facets of an octagon, i.e., the template coincides with [`OctDirections`](@ref).

```jldoctest dirs_BoxDiag
julia> collect(dirs)
8-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [-1.0, 1.0]
 [1.0, -1.0]
 [-1.0, -1.0]
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

The numeric type can be specified as well:

```jldoctest
julia> dirs = BoxDiagDirections{Rational{Int}}(10)
BoxDiagDirections{Rational{Int64}, Vector{Rational{Int64}}}(10)

julia> length(dirs)
1044
```
