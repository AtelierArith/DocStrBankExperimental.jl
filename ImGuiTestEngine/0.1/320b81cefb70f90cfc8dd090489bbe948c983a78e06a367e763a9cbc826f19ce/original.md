```julia
ItemCheck(test_ref::Union{Int64, String})
ItemCheck(test_ref::Union{Int64, String}, ctx)

```

Check an item.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemCheck("My checkbox")
end
```
