```
lowerbd{T}(A::ReMat{T})
```

行列 `A` に関連するパラメータ `θ` の下限を返します。

これは、列優先順序での `A.λ` の下三角の要素です。対角成分の下限は `0` です。非対角成分の下限は `-Inf` です。
