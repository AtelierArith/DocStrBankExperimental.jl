```
mutable struct CxxTensor <: AbstractArray{Cdouble, 3}
```

Wrapper for `CxxPtr{CxxPtr{CxxPtr{Cdouble}}}`, which is used as `double***` in C++.
