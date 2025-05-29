```
algebraic_closure(::QQField)
```

Return a field representing the algebraic closure of the field of rational numbers.

# Examples

```jldoctest
julia> K = algebraic_closure(QQ)
Algebraic closure of rational field

julia> sqrt(K(2))
Root 1.41421 of x^2 - 2
```
