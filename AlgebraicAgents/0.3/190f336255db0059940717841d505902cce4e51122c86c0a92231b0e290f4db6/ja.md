```
@control opera call [id]
@control agent call [id]
```

システムにコントロールを追加します。オプションで、アクションのテキスト識別子 `id` を提供します。

`call` は式であり、無名の引数なし関数 `() -> call` にラップされます。

[`Opera`](@ref) も参照してください。

# 例

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
@control system control(system) "temperature control"
```
