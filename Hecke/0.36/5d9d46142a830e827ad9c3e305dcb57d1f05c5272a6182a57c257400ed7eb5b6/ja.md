```
representation_matrix(x::AlgAssAbsOrdElem, action::Symbol = :left) -> ZZMatrix
```

`order(x)`の基底に関して$x$との乗法を表す行列を返します。`action == :left`の場合は左からの乗法であり、`action == :right`の場合は右からの乗法です。
