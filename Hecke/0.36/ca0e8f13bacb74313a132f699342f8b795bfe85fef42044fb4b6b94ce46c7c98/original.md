```
localization(OK::AbsNumFieldOrder{AbsSimpleNumField,T}, S::AbsNumFieldOrderIdeal{AbsSimpleNumField,T}; cached=true, comp = false) where {T <: AbsSimpleNumFieldElem}
```

Returns the localization of the order $OK$ at the ideal $S$. If `cached == true` (the default) then the resulting localization parent object is cached and returned for any subsequent calls to the constructor with the same order $OK$ and ideal $S$. `comp == false` means primes dividing $S$ are invertible, `comp == true` means all primes not dividing $S$ become units.
