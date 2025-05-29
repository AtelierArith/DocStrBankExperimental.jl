```
QQBarField <: Field
QQBarFieldElem <: FieldElem
```

The algebraic closure $\overline{\mathbb Q}$ of the rationals $\mathbb Q$ and its elements. This is a singleton type, meaning that there is a unique global instance of this field, which can be obtained via `algebraic_closure(QQ)`.

```jldoctest
julia> K = algebraic_closure(QQ)
Algebraic closure of rational field

julia> sqrt(K(2))
Root 1.41421 of x^2 - 2

julia> QQBar(2//3)
Root 0.666667 of 3x - 2

julia> sinpi(QQBar(2//3))
Root 0.866025 of 4x^2 - 3
```
