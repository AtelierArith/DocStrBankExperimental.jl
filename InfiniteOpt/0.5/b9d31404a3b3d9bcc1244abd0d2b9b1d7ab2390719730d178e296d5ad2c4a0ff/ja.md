```
optimizer_model_key(model::JuMP.Model)::Any
```

最適化モデル `model` で使用される拡張キーを返します。`model.ext` に複数のキーが含まれている場合はエラーになります。これは内部使用および拡張のために意図されています。拡張に対しては、[`build_optimizer_model!`](@ref) などの適切な最適化モデル関数にディスパッチするために使用されます。これは内部メソッドとして意図されています。公開メソッドについては、[`optimizer_model_key`](@ref optimizer_model_key(::InfiniteModel)) を参照してください。
