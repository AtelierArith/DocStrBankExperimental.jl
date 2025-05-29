```
mutable struct CxxMatrix <: AbstractMatrix{Cdouble}
```

Wrapper for `CxxPtr{CxxPtr{Cdouble}}`, which is used as `double**` in C++.
