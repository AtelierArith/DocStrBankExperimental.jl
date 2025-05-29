```
mul!(c::ZZ2Vector, a::ZZ2Matrix, b::AbstractVector{<:Number}, α::Number = ZZ2(1), β::Number = ZZ2(0)) -> c
```

Store the combined matrix-vector multiply-add `α a*b + β c` in `c` and return `c`. With the default values of `α` and `β` the product `a*b` is computed. The elements of `b` as well as `α` and `β` must be convertible to `ZZ2`.

This function is re-exported from the module `LinearAlgebra`.
