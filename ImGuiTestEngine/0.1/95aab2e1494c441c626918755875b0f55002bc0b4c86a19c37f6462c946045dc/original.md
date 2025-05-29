```julia
Stop(engine::ImGuiTestEngine.Engine)

```

Stop a test engine context.

# Examples

```julia
ctx = ig.CreateContext()
engine = te.CreateContext()
te.Start(engine, ctx)
te.Stop(engine)
```
