```
@nested_log(symbol, expr)
```

ネストされた形でデータをログすることを可能にするマクロです。

# 例

  * 例 1

```julia
@nested_log :subsystem dynamics!(dx.sub, x.sub, p.sub, t)
```

は `dynamics!(dx.sub, x.sub, p.sub, t)` からのデータを `__LOGGER__.subsystem` としてログします。

  * 例 2

```julia
@nested_log :subsystem state = x
```

# 注意

同じキーで値を割り当てると、次のようなエラーが発生します。

```julia
ERROR: MethodError: no method matching recursive_merge(::Int64, ::Int64)
```
