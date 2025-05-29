```
factor(a::T) where T <: RingElement -> Fac{T}
```

$ a $ を不可約要素に因数分解した結果を `Fac{T}` として返します。因数分解における不可約要素は互いに素です。
