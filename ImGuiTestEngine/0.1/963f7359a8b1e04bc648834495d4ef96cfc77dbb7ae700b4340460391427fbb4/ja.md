```julia
MouseMove(test_ref::Union{Int64, String})
MouseMove(test_ref::Union{Int64, String}, ctx)

```

`test_ref`にマウスを移動します。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseMove("My button")
end
```
