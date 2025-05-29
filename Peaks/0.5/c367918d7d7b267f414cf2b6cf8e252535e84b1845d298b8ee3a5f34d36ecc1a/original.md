```
isminima(i, x[, w=1; strict=true]) -> Bool
```

Test if `i` is a minima in `x`, where the minima `i` is either the minimum of `x[i-w:i+w]` or the first index of a plateau.

A plateau is defined as a minima with consecutive equal (`==`) minimal values which are bounded by greater values immediately before and after the consecutive minimal values.

See also: [`findnextminima`](@ref)
