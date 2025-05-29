```
maxima(x[, w=1; strict=true]) -> Vector{eltype(x)}
```

Find the values of local maxima in `x`, where each maxima `i` is either the maximum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the consecutive maximal values.

See also: [`argmaxima`](@ref), [`findnextmaxima`](@ref), [`minima`](@ref)
