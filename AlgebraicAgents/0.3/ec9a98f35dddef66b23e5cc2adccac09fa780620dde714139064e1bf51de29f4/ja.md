```
getobservable(agent, args...)
```

エージェントの観測可能な値を取得します。

# 例

```julia
getobservable(getagent(agent, "../model"), "observable_name")
getobservable(getagent(agent, "../model"), 1)
```
