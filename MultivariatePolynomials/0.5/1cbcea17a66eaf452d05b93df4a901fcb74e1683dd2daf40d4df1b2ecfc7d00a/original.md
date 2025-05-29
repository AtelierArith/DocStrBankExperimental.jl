```
struct InverseLexOrder <: AbstractMonomialOrdering end
```

Inverse Lex Order defined in [CLO13, Exercise 2.2.6, p. 61] where it is abbreviated as *invlex*. It corresponds to [`LexOrder`](@ref) but with the variables in reverse order.

The [`Graded`](@ref) version can be abbreviated as *grinvlex* order. It is defined in [BDD13, Definition 2.1] where it is called *Graded xel order*.

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**. [BDD13] Batselier, K., Dreesen, P., & De Moor, B. *The geometry of multivariate polynomial division and elimination*. SIAM Journal on Matrix Analysis and Applications, 34(1), 102-125, *2013*.
