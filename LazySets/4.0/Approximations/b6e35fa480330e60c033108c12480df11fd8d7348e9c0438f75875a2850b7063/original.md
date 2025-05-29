```
OctDirections{N, VN} <: AbstractDirections{N, VN}
```

Octagon directions representation.

### Fields

  * `n` – dimension

### Notes

Octagon directions consist of all vectors that are zero almost everywhere except in two dimensions $i$, $j$ (possibly $i = j$) where it is $±1$. In dimension $n$, there are $2n^2$ such directions.

### Examples

The template can be constructed by passing the dimension. For example, in dimension two:

```jldoctest dirs_Oct
julia> dirs = OctDirections(2)
OctDirections{Float64, SparseArrays.SparseVector{Float64, Int64}}(2)

julia> length(dirs) # number of directions
8
```

By default, the directions are represented as sparse vectors:

```jldoctest dirs_Oct
julia> eltype(dirs)
SparseArrays.SparseVector{Float64, Int64}
```

In two dimensions, the directions are normal to the facets of an octagon.

```jldoctest dirs_Oct
julia> first(dirs)
2-element SparseArrays.SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [2]  =  1.0

julia> Vector.(collect(dirs))
8-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [1.0, -1.0]
 [-1.0, 1.0]
 [-1.0, -1.0]
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

The numeric type can be specified as well:

```jldoctest
julia> dirs = OctDirections{Rational{Int}}(10)
OctDirections{Rational{Int64}, SparseArrays.SparseVector{Rational{Int64}, Int64}}(10)

julia> length(dirs)
200
```
