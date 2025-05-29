```
DiagDirections{N, VN} <: AbstractDirections{N, VN}
```

Diagonal directions representation.

### Fields

  * `n` – dimension

### Notes

Diagonal directions are vectors where all entries are ±1. In dimension $n$, there are in total $2^n$ such directions.

## Examples

The template can be constructed by passing the dimension. For example, in dimension two:

```jldoctest dirs_Diag
julia> dirs = DiagDirections(2)
DiagDirections{Float64, Vector{Float64}}(2)

julia> length(dirs) # number of directions
4
```

By default, each direction is represented as a regular `Vector`:

```jldoctest dirs_Diag
julia> eltype(dirs)
Vector{Float64} (alias for Array{Float64, 1})
```

In two dimensions, the directions defined by `DiagDirections` are normal to the facets of a ball in the 1-norm.

```jldoctest dirs_Diag
julia> collect(dirs)
4-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [-1.0, 1.0]
 [1.0, -1.0]
 [-1.0, -1.0]
```

The numeric type can be specified as well:

```jldoctest
julia> dirs = DiagDirections{Rational{Int}}(10)
DiagDirections{Rational{Int64}, Vector{Rational{Int64}}}(10)

julia> length(dirs)
1024
```
