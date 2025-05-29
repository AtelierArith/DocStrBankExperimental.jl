```
cospi(a::QQBarFieldElem)
```

代数的な数として $\cos(\pi a)$ を返します。この値が超越的である場合は例外をスローします。

# 例

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> x = cospi(QQBar(1//6))
Root 0.866025 of 4x^2 - 3
```
