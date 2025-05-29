```
optimize!(f, search_space, method;logger)
```

`method`の反復を実行し、結果を`method.status`に保存します。

### 例

```julia
f, bounds, _ = Metaheuristics.TestProblems.sphere();
method = ECA()
while !Metaheuristics.should_stop(method)
    optimize!(f, bounds, method)
end
result = Metaheuristics.get_result(method)
```

[`optimize`](@docs)も参照してください。
