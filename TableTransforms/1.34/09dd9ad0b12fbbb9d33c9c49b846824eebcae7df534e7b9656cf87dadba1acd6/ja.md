```
Satisfies(pred)
```

`pred(column)` が `true` を返す列を選択します。

# 例

```julia
Satisfies(allunique)
Satisfies(x -> sum(x) > 100)
Satisfies(x -> eltype(x) <: Integer)
```
