```
cospi(a::QQBarFieldElem)
```

Return $\cos(\pi a)$ as an algebraic number. Throws if this value is transcendental.

# Examples

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> x = cospi(QQBar(1//6))
Root 0.866025 of 4x^2 - 3
```
