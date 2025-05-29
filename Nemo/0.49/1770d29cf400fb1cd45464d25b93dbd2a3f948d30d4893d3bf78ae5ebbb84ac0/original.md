```
sinpi(a::QQBarFieldElem)
```

Return $\sin(\pi a)$ as an algebraic number. Throws if this value is transcendental.

# Examples

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> x = sinpi(QQBar(1//3))
Root 0.866025 of 4x^2 - 3
```
