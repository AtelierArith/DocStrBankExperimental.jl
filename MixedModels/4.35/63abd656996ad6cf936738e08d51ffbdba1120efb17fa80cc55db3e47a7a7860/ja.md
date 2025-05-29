```
restorereplicates(f, m::MixedModel{T})
restorereplicates(f, m::MixedModel{T}, ftype::Type{<:AbstractFloat})
restorereplicates(f, m::MixedModel{T}, ctype::Type{<:MixedModelFitCollection{S}})
```

`f`から複製を復元し、`m`を使用して[`MixedModelFitCollection`](@ref)の希望するサブタイプを作成します。

`f`は`Arrow.Table`によってサポートされる任意のエンティティであることができます。`m`はフィッティングされている必要はありませんが、保存された複製のソースと同じ構造で構築されている必要があります。

2引数のメソッドは、`m`と同じeltypeを持つ[`MixedModelBootstrap`](@ref)を構築します。eltypeが3番目の引数として指定されている場合、`MixedModelBootstrap`が返されます。`MixedModelFitCollection`のサブタイプが3番目の引数として指定されている場合、それが返り値の型になります。

[`savereplicates`](@ref)、[`restoreoptsum!`](@ref)も参照してください。
