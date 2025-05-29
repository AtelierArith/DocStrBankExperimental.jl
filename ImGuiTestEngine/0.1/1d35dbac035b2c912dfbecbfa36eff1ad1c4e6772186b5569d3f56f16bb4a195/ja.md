```julia
ItemDoubleClick(test_ref::Union{Int64, String})
ItemDoubleClick(test_ref::Union{Int64, String}, ctx)

```

参照をダブルクリックするシミュレーションを行います。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemDoubleClick("My selectable")
end
```
