```
fill_in_supports!(prefs::AbstractArray{<:DependentParameterRef};
                  [num_supports::Int = DefaultNumSupports,
                   modify::Bool = true])::Nothing
```

依存する無限パラメータ `prefs` のコンテナに対してサポートポイントを自動的に生成します。`generate_and_add_supports!` に従って、パラメータに対して最大 `num_supports` まで生成します。サポートが存在し、`modify = false` の場合は何も追加しません。ユーザー定義のドメインタイプを使用する拡張は、必要に応じて [`generate_and_add_supports!`](@ref) および/または [`generate_support_values`](@ref) を拡張する必要があります。無限ドメインタイプが認識されない場合はエラーが発生します。

**例**

```julia-repl
julia> fill_in_supports!(x, num_supports = 4)

julia> supports(x)
2×4 Array{Float64,2}:
 0.0  0.333  0.667  1.0
 0.0  0.333  0.667  1.0
```
