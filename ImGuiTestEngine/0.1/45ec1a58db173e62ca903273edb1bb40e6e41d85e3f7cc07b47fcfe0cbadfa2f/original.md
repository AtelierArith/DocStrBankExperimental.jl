```julia
SetRef(test_ref::Union{Int64, String})
SetRef(test_ref::Union{Int64, String}, ctx)

```

Set the current reference. For more information on references see the [upstream documentation](https://github.com/ocornut/imgui_test_engine/wiki/Named-References).

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    SetRef("My Window")
end
```

Note that `test_ref` is *always* treated as an absolute reference:

```julia
@register_test(engine, "foo", "bar") do ctx
    SetRef("My Window/quux") # This will set the reference to `//My Window/quux`

    # These two calls will not work
    SetRef("My Window") # Set the reference to `//My Window`
    SetRef("quux")      # Try to set the reference to `//quux`
end
```
