```julia
MouseMove(test_ref::Union{Int64, String})
MouseMove(test_ref::Union{Int64, String}, ctx)

```

Move the mouse to `test_ref`.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    MouseMove("My button")
end
```
