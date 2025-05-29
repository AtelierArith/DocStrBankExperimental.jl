```
struct Reverse{O<:AbstractMonomialOrdering} <: AbstractMonomialOrdering
    reverse_order::O
end
```

モノミアル順序は `cmp(o::Reverse, a, b) where {O} = cmp(o.reverse_order, b, a)` によって定義されます。

逆レキシコグラフィック順序は [CLO13, Exercise 2.2.9, p. 61] で定義され、*rinvlex* と略されます。これは `Reverse{InverseLexOrder}` として得られます。

グレード逆レキシコグラフィック順序は *grevlex* 順序と略され、[CLO13, Definition 2.2.6, p. 58] で定義され、`Graded{Reverse{InverseLexOrder}}` として得られます。

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**.
