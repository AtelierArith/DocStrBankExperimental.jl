```
findnextmaxima(x, i[, w=1; strict=true]) -> Int
```

Find the index of the next maxima in `x` after or including `i`, where the maxima `i` is either the maximum of `x[i-w:i+w]` or the first index of a plateau. Returns `lastindex(x) + 1` if no maxima occur after `i`.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the consecutive maximal values.

When `strict == true`, no elements in `x[i-w:i+w]` may be `missing` or `NaN`, and the bounds of a plateau must exist. For `strict == false`, a maxima is the maximum of all non-`NaN` or `missing` elements in `x[i-w:i+w]`, and plateau bounds are assumed to exist (i.e. `missing`, `NaN`, or either end of the array, `x[begin-1]` or `x[end+1]`, may be treated as the bounds of a plateau).

See also: [`argmaxima`](@ref)

# Examples

```jldoctest
julia> findnextmaxima([0,2,0,1,1,0], 2)
2

julia> findnextmaxima([0,2,0,1,1,0], 3)
4

```
