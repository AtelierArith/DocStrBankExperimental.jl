```
generate_and_add_supports!(pref::IndependentParameterRef,
                           domain::AbstractInfiniteDomain,
                           [method::Type{<:AbstractSupportLabel}];
                           [num_supports::Int = DefaultNumSupports])::Nothing
```

独立パラメータ `pref` のために [`generate_support_values`](@ref) を介してサポートを生成し、それを `pref` に追加します。これは、[`fill_in_supports!`](@ref fill_in_supports!(::IndependentParameterRef)) のための拡張可能な内部メソッドとして意図されています。ユーザー定義の無限ドメインを使用するほとんどの拡張は、通常、[`generate_support_values`](@ref) を拡張することでこれを有効にできます。無限ドメインタイプが認識されない場合はエラーが発生します。
