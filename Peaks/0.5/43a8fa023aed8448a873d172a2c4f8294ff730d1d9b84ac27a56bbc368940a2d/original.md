```
argminima(x[, w=1; strict=false]) -> Vector{Int}
```

Find the indices of local minima in `x`, where each minima `i` is either the minimum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the consecutive minimal values.

When `strict == true`, no elements in `x[i-w:i+w]` may be `missing` or `NaN`, and the bounds of a plateau must exist. For `strict == false`, a minima is the minimum of all non-`NaN` or `missing` elements in `x[i-w:i+w]`, and plateau bounds are assumed to exist (i.e. `missing`, `NaN`, or either end of the array, `x[begin-1]` or `x[end+1]`, may be treated as the bounds of a plateau).

See also: [`findminima`](@ref), [`findnextminima`](@ref)

# Examples

```jldoctest
julia> argminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> argminima([2,3,1,1])
Int64[]

julia> argminima([2,3,1,1]; strict=false)
2-element Vector{Int64}:
 1
 3
```
