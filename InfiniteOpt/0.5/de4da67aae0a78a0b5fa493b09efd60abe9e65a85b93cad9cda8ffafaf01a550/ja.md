```
`prefs`のために[`generate_support_values`](@ref)を介してサポートを生成し、それらを`pref`に追加します。これは、[`fill_in_supports!`](@ref fill_in_supports!(::AbstractArray{<:DependentParameterRef}))のための拡張可能な内部メソッドとして意図されています。ユーザー定義の無限ドメインを使用するほとんどの拡張は、通常、[`generate_support_values`](@ref)を拡張することでこれを有効にできます。しかし、無限パラメータのセットにサポートを追加するだけではなく、より複雑な操作を行う必要がある場合には、これを拡張する必要があるかもしれません。無限ドメインタイプが認識されない場合はエラーが発生します。
```
