```
struct ScalarCondition{U,FT<:AbstractFeature,M<:ScalarMetaCondition{FT}} <: AbstractScalarCondition{FT}
    metacond::M
    a::U
end
```

計算された特徴値（`ScalarMetaCondition`を参照）と閾値値`a`を比較するスカラー条件。これは、論理データセットのインスタンスの世界で評価できます。

例えば：$min[V1] ≥ 10$、これは「この世界の中で、変数1の最小値は10以上である。」という意味です。この場合、特徴は[`VariableMin`](@ref)オブジェクトです。

また、[`AbstractScalarCondition`](@ref)、[`ScalarMetaCondition`](@ref)も参照してください。
