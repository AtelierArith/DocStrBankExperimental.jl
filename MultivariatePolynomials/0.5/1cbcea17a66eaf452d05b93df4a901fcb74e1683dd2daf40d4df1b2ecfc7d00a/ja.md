```
struct InverseLexOrder <: AbstractMonomialOrdering end
```

逆レキシコ順序は[CLO13, 演習 2.2.6, p. 61]で定義されており、*invlex*と略されます。これは[`LexOrder`](@ref)に対応しますが、変数が逆順になっています。

[`Graded`](@ref)バージョンは*grinvlex*順序と略されます。これは[BDD13, 定義 2.1]で定義されており、*Graded xel order*と呼ばれています。

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**. [BDD13] Batselier, K., Dreesen, P., & De Moor, B. *The geometry of multivariate polynomial division and elimination*. SIAM Journal on Matrix Analysis and Applications, 34(1), 102-125, *2013*.
