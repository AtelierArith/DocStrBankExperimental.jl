```
argmaxima(x[, w=1; strict=true]) -> Vector{Int}
```

Find the indices of local maxima in `x`, where each maxima `i` is either the maximum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the consecutive maximal values.

When `strict == true`, no elements in `x[i-w:i+w]` may be `missing` or `NaN`, and the bounds of a plateau must exist. For `strict == false`, a maxima is the maximum of all non-`NaN` or `missing` elements in `x[i-w:i+w]`, and plateau bounds are assumed to exist (i.e. `missing`, `NaN`, or either end of the array, `x[begin-1]` or `x[end+1]`, may be treated as the bounds of a plateau).

See also: [`findmaxima`](@ref), [`findnextmaxima`](@ref), [`argminima`](@ref)

# Examples

```jldoctest
julia> argmaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> argmaxima([2,0,1,1])
Int64[]

julia> argmaxima([2,0,1,1]; strict=false)
2-element Vector{Int64}:
 1
 3
```
