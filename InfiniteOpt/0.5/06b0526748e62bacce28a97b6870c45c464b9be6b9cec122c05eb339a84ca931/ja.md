```
fill_in_supports!(pref::IndependentParameterRef;
                  [num_supports::Int = DefaultNumSupports])::Nothing
```

特定の独立パラメータ `pref` のためにサポートポイントを自動的に生成します。パラメータのために `num_supports` を生成します。サポートは、基盤となる無限のドメインが `IntervalDomain` の場合は均等に生成され、ドメインが `UniDistributionDomain` の場合は分布に応じてランダムに生成されます。サポートがあり、`modify = false` の場合は何も追加しません。ユーザー定義のドメインタイプを使用する拡張は、必要に応じて [`generate_and_add_supports!`](@ref) および/または [`generate_support_values`](@ref) を拡張する必要があります。無限ドメインタイプが認識されない場合はエラーが発生します。

**例**

```julia-repl
julia> fill_in_supports!(x, num_supports = 4)

julia> supports(x)
4-element Array{Number,1}:
 0.0
 0.333
 0.667
 1.0

```
