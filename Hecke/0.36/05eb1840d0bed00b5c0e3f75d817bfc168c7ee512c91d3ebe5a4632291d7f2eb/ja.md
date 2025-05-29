```
representation_matrix(a::AbstractAssociativeAlgebraElem, action::Symbol = :left) -> MatElem
```

`algebra(a)`の基底に関する$a$との乗法を表す、`base_ring(algebra(a))`上の行列を返します。`action`が`:left`の場合は左からの乗法、`:right`の場合は右からの乗法です。
