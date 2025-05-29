```
findnextminima(x, i[, w=1, strict=true]) -> Int
```

Find the index of the next minima in `x`, after or including `i`, where the minima `i` is either the minimum of `x[i-w:i+w]` or the first index of a plateau. Returns `lastindex(x) + 1` if no minima occur after `i`.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the consecutive minimal values.

When `strict == true`, no elements in `x[i-w:i+w]` may be `missing` or `NaN`, and the bounds of a plateau must exist. For `strict == false`, a minima is the minimum of all non-`NaN` or `missing` elements in `x[i-w:i+w]`, and plateau bounds are assumed to exist (i.e. `missing`, `NaN`, or either end of the array, `x[begin-1]` or `x[end+1]`, may be treated as the bounds of a plateau).

See also: [`argminima`](@ref)

# Examples

```jldoctest
julia> findnextminima([3,2,3,1,1,3], 2)
2

julia> findnextminima([3,2,3,1,1,3], 3)
4

```
