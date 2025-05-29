```julia
ItemCheck(test_ref::Union{Int64, String})
ItemCheck(test_ref::Union{Int64, String}, ctx)

```

アイテムをチェックします。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemCheck("My checkbox")
end
```
