```julia
ComboClickAll(test_ref::Union{Int64, String})
ComboClickAll(test_ref::Union{Int64, String}, ctx)

```

Click on all items in a combo box.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ComboClickAll("My combo")
end
```
