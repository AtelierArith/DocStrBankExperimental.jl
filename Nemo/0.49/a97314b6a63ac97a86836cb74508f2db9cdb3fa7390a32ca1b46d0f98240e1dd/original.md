```
sincospi(a::QQBarFieldElem)
```

Return $\sin(\pi a)$ and $\cos(\pi a)$ as a pair of algebraic numbers. Throws if either value is transcendental.

# Examples

```jldoctest
julia> QQBar = algebraic_closure(QQ);

julia> s, c = sincospi(QQBar(1//3))
(Root 0.866025 of 4x^2 - 3, Root 0.500000 of 2x - 1)
```
