```
struct Graded{O<:AbstractMonomialOrdering} <: AbstractMonomialOrdering
    same_degree_ordering::O
end
```

Monomial ordering defined by:

  * `degree(a) == degree(b)` then the ordering is determined by `same_degree_ordering`,
  * otherwise, it is the ordering between the integers `degree(a)` and `degree(b)`.
