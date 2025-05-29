```
TransformQuery(name, query)
```

シンプルな変換クエリ; エージェントをアンダースコア `_` を介して参照します。

参照: [`@transform`](@ref).

# 例

```julia
agent |> @transform(name=_.name)
agent |> @transform(name=_.name, _.age)
```
