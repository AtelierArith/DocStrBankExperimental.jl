```
abstract type AbstractMonomialOrdering end
```

モノミアル順序のための抽象型 [CLO13, 定義 2.2.1, p. 55] に定義されています。

順序 `ordering::AbstractMonomialOrdering` と指数ベクトル `e1` と `e2` が与えられたとき、`cmp(ordering, e1, e2)` は、`e1` が順序で `e2` の前にある場合は負の数を返し、`e2` が `e1` の前にある場合は正の数を返し、等しい場合は 0 を返します。便利のために、`ordering(e1, e2)` は `cmp(ordering, e1, e2)` が負であるかどうかを示す `Bool` を返します。

[CLO13] Cox, D., Little, J., & OShea, D. *Ideals, varieties, and algorithms: an introduction to computational algebraic geometry and commutative algebra*. Springer Science & Business Media, **2013**.
