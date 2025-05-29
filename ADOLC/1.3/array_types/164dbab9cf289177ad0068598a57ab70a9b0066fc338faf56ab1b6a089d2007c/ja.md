```
mutable struct CxxTensor <: AbstractArray{Cdouble, 3}
```

`CxxPtr{CxxPtr{CxxPtr{Cdouble}}}`のラッパーで、C++では`double***`として使用されます。
