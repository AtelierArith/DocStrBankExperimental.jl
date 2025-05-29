```
start(args...)
```

Define starting values for parameters. For ensemble models, multiple values (one for each submodel/group) are needed.

# Examples

```julia
graph = @StenoGraph begin
    x → start(1)*y
end
```
