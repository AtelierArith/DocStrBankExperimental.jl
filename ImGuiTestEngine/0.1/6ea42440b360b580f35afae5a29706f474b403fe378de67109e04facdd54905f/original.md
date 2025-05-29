```julia
ItemClose(test_ref::Union{Int64, String})
ItemClose(test_ref::Union{Int64, String}, flags)
ItemClose(test_ref::Union{Int64, String}, flags, ctx)

```

Ensure an item is closed.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemClose("My menu")
end
```
