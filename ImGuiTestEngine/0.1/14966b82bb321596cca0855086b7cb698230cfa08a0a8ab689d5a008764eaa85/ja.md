```julia
OpenAndClose(test_ref::Union{Int64, String})
OpenAndClose(test_ref::Union{Int64, String}, ctx)

```

`test_ref`を開いてから閉じます。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    OpenAndClose("My section")
end
```
