```julia
QueueTest(
    engine::ImGuiTestEngine.Engine,
    test::ImGuiTestEngine.ImGuiTest
)
QueueTest(
    engine::ImGuiTestEngine.Engine,
    test::ImGuiTestEngine.ImGuiTest,
    run_flags
)

```

Queue a specific test for execution. If you're using the CImGui.jl renderloop it shouldn't be necessary to call this yourself.

# Examples

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar") do ctx
    @info "Hello world!"
end

te.QueueTest(engine, t)
```
