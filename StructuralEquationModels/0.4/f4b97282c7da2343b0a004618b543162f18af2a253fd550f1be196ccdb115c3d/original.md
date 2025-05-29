```
label(args...)
```

Label parameters. For ensemble models, multiple values (one for each submodel/group) are needed.

# Examples

```julia
graph = @StenoGraph begin
    x → label(:a)*y
end
```
