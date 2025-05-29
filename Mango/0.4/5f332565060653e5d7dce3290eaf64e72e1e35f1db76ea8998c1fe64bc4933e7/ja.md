```
agent_composed_of(roles::Role...; base_agent::Union{Nothing,Agent}=nothing)
```

与えられた役割 `roles...` で構成されるエージェントを作成します。

`base_agent` が提供されていない場合、使用されるエージェント構造体は空の構造体であり、役割のコンテナとしてのみ使用されます。関数によってエージェントが返されます。

# 例

```julia
agent = agent_composed_of(RoleA(), RoleB(), RoleC())
```
