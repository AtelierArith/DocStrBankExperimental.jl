```
filter(agent::AbstractAlgebraicAgent, queries...)
filter(agents::Vector{<:AbstractAlgebraicAgent}, queries...)
```

エージェントの階層に対してフィルタクエリを実行します。

# 例

```julia
filter(agent, f"_.age > 21 && _.name ∈ ['a', 'b']") # フィルタクエリ
```
