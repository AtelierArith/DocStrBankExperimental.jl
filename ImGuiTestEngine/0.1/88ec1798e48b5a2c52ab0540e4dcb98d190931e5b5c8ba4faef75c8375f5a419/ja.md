```julia
ComboClickAll(test_ref::Union{Int64, String})
ComboClickAll(test_ref::Union{Int64, String}, ctx)

```

コンボボックス内のすべてのアイテムをクリックします。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    ComboClickAll("My combo")
end
```
