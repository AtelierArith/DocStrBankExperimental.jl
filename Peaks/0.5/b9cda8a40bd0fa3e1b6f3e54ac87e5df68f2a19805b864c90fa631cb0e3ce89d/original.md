```
findminima(x[, w=1; strict=true]) -> (;indices, heights, data)
```

Find the indices and values of local minima in `x`, where each minima `i` is either the minimum of `x[i-w:i+w]` or the first index of a plateau.

Returns a `NamedTuple` contains the fields `indices`, `heights`, `data`, which are equivalent to `heights = data[indices]`. The `data` field is a reference (not a copy) to the argument `x`.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the consecutive minimal values.

See also: [`argminima`](@ref), [`findnextminima`](@ref)

# Examples

```jldoctest
julia> data = [1, 5, 1, 3, 2];

julia> valleys = findminima(data)
(indices = [3], heights = [1], data = [1, 5, 1, 3, 2])
```
