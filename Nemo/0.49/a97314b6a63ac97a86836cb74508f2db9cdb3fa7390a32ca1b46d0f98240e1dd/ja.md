```
sincospi(a::QQBarFieldElem)
```

返す $\sin(\pi a)$ と $\cos(\pi a)$ を代数的数のペアとして。いずれかの値が超越的である場合は例外をスローします。

# 例

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> s, c = sincospi(QQBar(1//3))
(Root 0.866025 of 4x^2 - 3, Root 0.500000 of 2x - 1)
```
