```
BoxDirections{N, VN} <: AbstractDirections{N, VN}
```

Box directions representation.

### Fields

  * `n` – dimension

### Notes

Box directions can be seen as the vectors where only one entry is ±1, and all other entries are 0. In dimension $n$, there are $2n$ such directions.

The default vector representation used in this template is a `ReachabilityBase.Arrays.SingleEntryVector`, although other implementations can be used such as a regular `Vector` and a `SparseVector`.

### Examples

The template can be constructed by passing the dimension. For example, in dimension two:

```jldoctest dirs_Box
julia> dirs = BoxDirections(2)
BoxDirections{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}(2)

julia> length(dirs)
4
```

By default, each direction is represented as a `SingleEntryVector`, i.e., a vector with only one non-zero element,

```jldoctest dirs_Box
julia> eltype(dirs)
ReachabilityBase.Arrays.SingleEntryVector{Float64}
```

In two dimensions, the directions defined by `BoxDirections` are normal to the facets of a box.

```jldoctest dirs_Box
julia> collect(dirs)
4-element Vector{ReachabilityBase.Arrays.SingleEntryVector{Float64}}:
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

The numeric type can be specified as well:

```jldoctest
julia> dirs = BoxDirections{Rational{Int}}(10)
BoxDirections{Rational{Int64}, ReachabilityBase.Arrays.SingleEntryVector{Rational{Int64}}}(10)

julia> length(dirs)
20
```
