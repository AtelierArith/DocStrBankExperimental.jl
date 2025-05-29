```
num_parameters(model::InfiniteModel,
               [type::Type{InfOptParameter} = InfOptParameter])::Int
```

モデルに割り当てられた `InfiniteOpt` パラメータの数を返します。デフォルトでは、無限および有限パラメータの合計数が返されます。特定のタイプの数は、`type` を介して [`InfOptParameter`](@ref) の具体的なパラメータタイプを指定することで取得されます。タイプのオプションには以下が含まれます：

  * `InfOptParameter`: すべてのパラメータ
  * `ScalarParameter`: すべてのスカラーパラメータ
  * `InfiniteParameter`: すべての無限パラメータ
  * `FiniteParameter`: すべての有限パラメータ
  * `IndependentParameter`: すべての独立した無限パラメータ
  * `DependentParameters`: すべての従属した無限パラメータ

**例**

```julia-repl
julia> num_parameters(model)
3

julia> num_parameters(model, IndependentParameter)
2
```
