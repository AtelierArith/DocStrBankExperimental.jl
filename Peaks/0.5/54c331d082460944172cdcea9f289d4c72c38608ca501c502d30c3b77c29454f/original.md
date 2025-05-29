```
minima(x[, w=1; strict=true]) -> Vector{eltype(x)}
```

Find the values of local minima in `x`, where each minima `i` is either the minimum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the consecutive minimal values.

See also: [`argminima`](@ref), [`findnextminima`](@ref)
