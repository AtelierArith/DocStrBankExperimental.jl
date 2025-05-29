```julia
OpenAndClose(test_ref::Union{Int64, String})
OpenAndClose(test_ref::Union{Int64, String}, ctx)

```

Open and then close `test_ref`.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    OpenAndClose("My section")
end
```
