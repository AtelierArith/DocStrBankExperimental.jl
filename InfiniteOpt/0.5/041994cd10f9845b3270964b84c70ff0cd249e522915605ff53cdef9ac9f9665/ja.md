```
all_parameters(model::InfiniteModel,
               type::Type{InfOptParameter} = InfOptParameter
               )::Vector{GeneralVariableRef}
```

モデルに割り当てられたすべての `InfiniteOpt` パラメータのリストを返します。デフォルトでは、すべての無限および有限パラメータが返されます。特定のタイプに対する検索は、`type` を介して [`InfOptParameter`](@ref) の具体的なパラメータタイプを指定することで得られます。タイプのオプションには以下が含まれます：

  * `InfOptParameter`: すべてのパラメータ
  * `ScalarParameter`: すべてのスカラーパラメータ
  * `InfiniteParameter`: すべての無限パラメータ
  * `FiniteParameter`: すべての有限パラメータ
  * `IndependentParameter`: すべての独立した無限パラメータ
  * `DependentParameters`: すべての従属した無限パラメータ

**例**

```julia-repl
julia> all_parameters(model)
4-element Array{GeneralVariableRef,1}:
 t
 x[1]
 x[2]
 alpha

julia> all_parameters(model, FiniteParameter)
1-element Array{GeneralVariableRef,1}:
 alpha
```
