```
QQField <: FracField{ZZRingElem}
QQFieldElem <: FracFieldElem{ZZRingElem}
```

The field of rationals $\mathbb Q$ and its elements. For convenience, we predefine the global variable `const QQ = QQField()`.

# Examples

```jldoctest
julia> QQ(2//3) == ZZ(2)//ZZ(3)
true

julia> QQ(1//6) - QQ(1//7)
1//42
```
