```
sinpi(a::QQBarFieldElem)
```

代数的数として $\sin(\pi a)$ を返します。この値が超越数の場合は例外をスローします。

# 例

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> x = sinpi(QQBar(1//3))
Root 0.866025 of 4x^2 - 3
```
