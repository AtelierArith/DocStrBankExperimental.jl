```julia
ItemOpen(test_ref::Union{Int64, String})
ItemOpen(test_ref::Union{Int64, String}, flags)
ItemOpen(test_ref::Union{Int64, String}, flags, ctx)

```

Ensure an item is opened.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemOpen("My menu")
end
```
