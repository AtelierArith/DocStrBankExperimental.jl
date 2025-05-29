```
Amodule(M::Vector{<:MatElem})
```

Given a list `M` of square matrices over a field $K$, construct the module for the free algebra with the generators acting via `M[i]` from the right.

Note that the free algebra will not be constructed and the resulting object has no associated algebra.
