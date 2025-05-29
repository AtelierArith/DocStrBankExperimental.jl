```
findmaxima(x[, w=1; strict=true]) -> (;indices, heights, data)
```

Find the indices and values of local maxima in `x`, where each maxima `i` is either the maximum of `x[i-w:i+w]` or the first index of a plateau.

Returns a `NamedTuple` contains the fields `indices`, `heights`, `data`, which are equivalent to `heights = data[indices]`. The `data` field is a reference (not a copy) to the argument `x`.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the consecutive maximal values.

See also: [`argmaxima`](@ref), [`findnextmaxima`](@ref), [`findminima`](@ref)

# Examples

```jldoctest
julia> data = [1, 5, 1, 3, 2];

julia> pks = findmaxima(data)
(indices = [2, 4], heights = [5, 3], data = [1, 5, 1, 3, 2])
```
