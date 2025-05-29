```
struct Reverse{O<:AbstractMonomialOrdering} <: AbstractMonomialOrdering
    reverse_order::O
end
```

Monomial ordering defined by `cmp(o::Reverse, a, b) where {O} = cmp(o.reverse_order, b, a)`.

Reverse Lex Order defined in [CLO13, Exercise 2.2.9, p. 61] where it is abbreviated as *rinvlex*. can be obtained as `Reverse{InverseLexOrder}`.

The Graded Reverse Lex Order often abbreviated as *grevlex* order defined in [CLO13, Definition 2.2.6, p. 58] can be obtained as `Graded{Reverse{InverseLexOrder}}`.

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**.
