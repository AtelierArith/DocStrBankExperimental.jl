```
factor_squarefree(a::T) where T <: RingElement -> Fac{T}
```

$ a $ を平方フリー要素に因数分解し、`Fac{T}` として返します。因数分解における平方フリー要素は互いに素です。
