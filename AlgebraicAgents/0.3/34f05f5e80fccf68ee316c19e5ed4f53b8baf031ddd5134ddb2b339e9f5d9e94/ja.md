```
FilterQuery(query)
```

シンプルなプロパティクエリ; エージェントをアンダースコア `_` を介して参照します。

エージェントに対するクエリはエラーを引き起こす可能性があります。その場合、エージェントはデフォルトでフィルター条件に失敗します。

関連情報として [`@f_str`](@ref)、[`filter`](@ref) を参照してください。

# 例

```julia
filter(agents, f"_.age > 21 && _.name ∈ ['a', 'b']")
agents |> @filter _.age > 21 && _.name ∈ ['a', 'b']
```
