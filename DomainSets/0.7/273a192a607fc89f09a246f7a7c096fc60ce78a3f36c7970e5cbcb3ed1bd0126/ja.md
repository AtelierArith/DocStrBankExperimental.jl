```
ProductDomain(domains...)
ProductDomain{T}(domains...)
```

与えられたドメインの直積に数学的に一致する `ProductDomain` の具体的なサブタイプを返します。

返される具体的なサブタイプは `T` に依存します。`T` が提供されている場合、それはプロダクトドメインの eltype になります。`T` が提供されていない場合、引数から適切な選択が推測されます。

参照: [`VcatDomain`](@ref), [`VectorProductDomain`](@ref), [`TupleProductDomain`](@ref), [`Rectangle(a,b)`](@ref).
