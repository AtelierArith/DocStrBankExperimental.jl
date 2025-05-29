```julia
struct ZeroModel{T} <: ComradeBase.AbstractModel
```

Defines a model that is `empty` that is it return zero for everything.

# Notes

This returns 0 by using `FillArrays` so everything should be non-allocating
