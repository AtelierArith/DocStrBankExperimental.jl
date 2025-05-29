```julia
ItemClick(test_ref::Union{Int64, String})
ItemClick(
    test_ref::Union{Int64, String},
    button::CImGui.lib.ImGuiMouseButton_
)
ItemClick(
    test_ref::Union{Int64, String},
    button::CImGui.lib.ImGuiMouseButton_,
    ctx
)

```

Simulate a click on the reference.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    ItemClick("My button")
end
```
