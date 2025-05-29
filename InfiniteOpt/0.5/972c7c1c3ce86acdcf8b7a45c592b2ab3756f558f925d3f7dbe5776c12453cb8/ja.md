```
JuMP.set_upper_bound(pref::DependentParameterRef, upper::Real)::Nothing
```

`JuMP.set_upper_bound` 関数を拡張して、単一の依存無限パラメータに対応させます。この操作がサポートされている場合、無限ドメインの上限を更新します。この機能を利用しようとする無限スカラー領域の拡張は、`JuMP.set_upper_bound(domain::NewType, upper::Number)` を拡張する必要があります。これは [`set_infinite_domain`](@ref) を呼び出し、これが定義されていない場合はエラーになります。既存のサポートは削除されることに注意してください。

**例**

```julia-repl
julia> set_upper_bound(t, -1)

julia> upper_bound(t)
-1.0
```
