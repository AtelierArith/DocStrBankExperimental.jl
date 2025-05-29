```julia
ComboClick(test_ref::Union{Int64, String})
ComboClick(test_ref::Union{Int64, String}, ctx)

```

コンボボックスアイテムをクリックします。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    ComboClick("My combo/Item 1")
end
```
