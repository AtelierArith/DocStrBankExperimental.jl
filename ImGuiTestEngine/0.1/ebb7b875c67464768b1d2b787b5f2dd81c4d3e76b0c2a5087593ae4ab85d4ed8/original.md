```julia
QueueTests(engine::ImGuiTestEngine.Engine)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup
)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup,
    filter
)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup,
    filter,
    run_flags
)

```

Queue all tests in a specific group. If you're using the CImGui.jl renderloop it shouldn't be necessary to call this yourself.

# Examples

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar") do ctx
    @info "Hello world!"
end

# Queue all tests
te.QueueTests(engine)
```
