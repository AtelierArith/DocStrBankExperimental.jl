```
representation_matrix(x::AlgAssRelOrdElem, action::Symbol = :left) -> MatElem
```

`order(x)`の基底に関して$x$との乗算を表す行列を返します。`action`が`:left`の場合は左からの乗算、`:right`の場合は右からの乗算です。
