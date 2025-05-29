```
f"クエリ"
```

クエリ文字列をクエリインスタンスに変換します。詳細は[`FilterQuery`](@ref)を参照してください。

文字列の補間をサポートしています。

# 例

```julia
filter(agents, f"_.age > 1 && _.name ∈ ['a', 'b']")
i = 1; filter(agents, f"_.age > $i && _.name ∈ ['a', 'b']")
```
