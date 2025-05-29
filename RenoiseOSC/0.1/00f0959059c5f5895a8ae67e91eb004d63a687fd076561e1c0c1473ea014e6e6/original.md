```
luaeval(expr::AbstractString)
```

Evaluate a Lua expression inside Renoise's scripting environment.

# Example

```julia
luaeval("renoise.song().transport.bpm = 132")
```
