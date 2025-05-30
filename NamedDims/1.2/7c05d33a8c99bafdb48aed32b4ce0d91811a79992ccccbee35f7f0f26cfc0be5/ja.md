```
unname(A::NamedDimsArray) -> AbstractArray
unname(A) === A
```

次元名なしで入力配列 `A` を返します。

`NamedDimsArray` の場合、これは親配列を返し、`parent` を呼び出すのと同等ですが、他のものに対しては単に入力を返します。

`LowerTriangular`、`UpperTriangular` のような一部の `LinearAlgebra` ラッパーをサポートしており、`unname(x::UpperTriangular{T, <:NamedDimsArray}) == unname(parent(x))` です。
