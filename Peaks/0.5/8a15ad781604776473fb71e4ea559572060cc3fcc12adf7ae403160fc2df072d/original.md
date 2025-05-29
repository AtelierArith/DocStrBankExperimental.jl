```
ismaxima(i, x[, w=1; strict=true]) -> Bool
```

Test if `i` is a maxima in `x`, where the maxima `i` is either the maximum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a maxima with consecutive equal (`==`) maximal values which are bounded by lesser values immediately before and after the consecutive maximal values.

See also: [`findnextmaxima`](@ref)
