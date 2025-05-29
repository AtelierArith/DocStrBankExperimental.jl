```
all_pairs(parameters...; kwargs...)
```

返されるテストケースには、すべてのパラメータのペアが少なくとも一度は含まれていることを確認してください。

# 例

```julia
all_pairs([1, 2, 3], ["a", "b", "c"], [true, false])
```

参照: [`all_tuples`](@ref)
