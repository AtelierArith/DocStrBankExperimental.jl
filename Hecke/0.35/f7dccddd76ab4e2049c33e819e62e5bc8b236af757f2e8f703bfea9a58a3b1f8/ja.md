```
representation_matrix(x::AlgAssRelOrdElem, action::Symbol = :left) -> MatElem
```

$ x :との乗算を`order(x)`の基底に関して表す行列を返します。`action == :left`の場合は左からの乗算であり、`action == :right`の場合は右からの乗算です。
