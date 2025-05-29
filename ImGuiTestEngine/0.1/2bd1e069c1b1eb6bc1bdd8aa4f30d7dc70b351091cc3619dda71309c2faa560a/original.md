```julia
DestroyContext(engine::ImGuiTestEngine.Engine; throw)

```

Destroy a test engine context.

# Arguments

  * `throw=true`: Whether to throw an exception if the engine has already been destroyed.

# Examples

```julia
engine = te.CreateContext()
te.DestroyContext(engine)
```
