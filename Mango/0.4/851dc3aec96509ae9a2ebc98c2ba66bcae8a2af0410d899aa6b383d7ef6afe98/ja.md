```
add_agent_composed_of(container, roles::Role...; suggested_aid::Union{Nothing,String}=nothing, base_agent::Union{Nothing,Agent}=nothing)
```

与えられた役割 `roles...` で構成されるエージェントを作成し、エージェントを `container` に登録します。

`base_agent` が提供されていない場合、使用されるエージェント構造体は空の構造体であり、役割のコンテナとしてのみ使用されます。エージェントは関数によって返されます。

# 例

```julia
agent = add_agent_composed_of(your_container, RoleA(), RoleB(), RoleC())
```
