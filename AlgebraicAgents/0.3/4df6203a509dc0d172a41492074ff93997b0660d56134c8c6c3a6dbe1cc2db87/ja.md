```
transform(agent::AbstractAlgebraicAgent, queries...)
tranform(agent::Vector{<:AbstractAlgebraicAgent}, queries...)
```

エージェントの階層内で変換クエリを実行します。

エージェントに対するクエリはエラーを引き起こす可能性があり、その場合、該当するエージェントの出力は結果から省略されます。

詳細は [`@transform`](@ref) を参照してください。

# 例

```julia
agent |> @transform(name=_.name)
agent |> @transform(name=_.name, _.age)
```
