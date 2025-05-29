```
default_basis(M::AbstractManifold, ::typeof(p); kwargs...)
default_basis(M::AbstractManifold; kwargs...)
```

多様体の接空間のデフォルト基底を提供します。これは、`M`上の異なる点`p`に特有のものです。両方のグローバルデフォルトは、`M`と同じ数値型の[`DefaultOrthonormalBasis`](@ref)です。

このメソッドは、`M`上に異なる逆引き戻しメソッドを提供する2つの異なる点の表現がある場合に、点の型`T`でより正確に指定することもできます。

## キーワード引数

  * `field::`[`AbstractNumbers`](@ref) 基底の係数のためのフィールド
