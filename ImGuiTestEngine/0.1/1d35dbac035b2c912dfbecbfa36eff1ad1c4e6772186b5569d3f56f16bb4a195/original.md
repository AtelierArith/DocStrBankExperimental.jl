```julia
ItemDoubleClick(test_ref::Union{Int64, String})
ItemDoubleClick(test_ref::Union{Int64, String}, ctx)

```

Simulate a double-click on the reference.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemDoubleClick("My selectable")
end
```
