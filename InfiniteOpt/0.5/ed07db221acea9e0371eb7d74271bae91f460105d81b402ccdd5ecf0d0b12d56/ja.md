```
optimizer_model_key(model::InfiniteModel)::Any
```

`model`の最適化モデルで使用される拡張キーを返します。`optimizer_model.ext`に複数のキーが含まれている場合はエラーになります。これは内部使用および拡張のために意図されています。拡張に対しては、[`build_optimizer_model!`](@ref)などの適切な最適化モデル関数にディスパッチするために使用されます。

**例**

```julia-repl
julia> optimizer_model_key(model)
:TransData
```
