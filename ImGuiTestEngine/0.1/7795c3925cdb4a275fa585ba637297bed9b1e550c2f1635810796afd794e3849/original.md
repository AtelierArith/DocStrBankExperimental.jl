```julia
MenuClick(test_ref::Union{Int64, String})
MenuClick(test_ref::Union{Int64, String}, ctx)

```

Click on a menu item.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    MenuClick("My menu")
end
```
