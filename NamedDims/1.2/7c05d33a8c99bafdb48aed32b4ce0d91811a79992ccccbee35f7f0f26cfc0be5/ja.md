```
unname(A::NamedDimsArray) -> AbstractArray
unname(A) === A
```

次のように、次元名なしで入力配列 `A` を返します。

`NamedDimsArray` の場合、これは親配列を返し、`parent` を呼び出すのと同等ですが、それ以外の場合は単に入力を返します。

いくつかのLinearAlgebraラッパーであるLowerTriangular、UpperTriangularをサポートしており、次のようになります： `unname(x::UpperTriangular{T, <:NamedDimsArray}) == unname(parent(x))`
