```
@register_test(engine, category::AbstractString, name::AbstractString)::ImGuiTest
@register_test(f::Function, engine,
               category::AbstractString, name::AbstractString)::ImGuiTest
```

Register a [`ImGuiTest`](@ref). Note that it will not be executed until the test is queued, either programmatically with [`QueueTests()`](@ref) or by the user running it manually through [`ShowTestEngineWindows()`](@ref).

# Examples

If you only need to set `TestFunc` you can use do-syntax:

```julia
engine = te.CreateContext()
@register_test(engine, "foo", "bar") do ctx
    @imtest ctx isa te.TestContext
end
```

To set `GuiFunc` as well you'll need to set the `GuiFunc` property:

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar")
t.GuiFunc = ctx -> begin
    ig.Begin("Foo")
    ig.End()
end
t.TestFunc = ctx -> @info "Hello world!"
```
