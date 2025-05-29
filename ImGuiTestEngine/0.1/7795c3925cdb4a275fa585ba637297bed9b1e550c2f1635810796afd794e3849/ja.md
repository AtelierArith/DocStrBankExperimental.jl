```julia
MenuClick(test_ref::Union{Int64, String})
MenuClick(test_ref::Union{Int64, String}, ctx)

```

メニュー項目をクリックします。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    MenuClick("My menu")
end
```
