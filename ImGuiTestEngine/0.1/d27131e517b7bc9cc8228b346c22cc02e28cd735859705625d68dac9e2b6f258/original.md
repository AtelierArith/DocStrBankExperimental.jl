```julia
Start(
    engine::ImGuiTestEngine.Engine,
    ctx::Ptr{CImGui.lib.ImGuiContext}
)

```

Start a test engine context. If you're using CImGui.jl's renderloop you *must not* call this, it will be called automatically for you.

# Examples

```julia
ctx = ig.CreateContext()
engine = te.CreateContext()
te.Start(engine, ctx)
```
