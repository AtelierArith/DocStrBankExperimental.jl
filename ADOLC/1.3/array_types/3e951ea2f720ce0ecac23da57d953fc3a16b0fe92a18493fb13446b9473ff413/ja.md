```
mutable struct CxxMatrix <: AbstractMatrix{Cdouble}
```

`CxxPtr{CxxPtr{Cdouble}}`のラッパーで、C++では`double**`として使用されます。
