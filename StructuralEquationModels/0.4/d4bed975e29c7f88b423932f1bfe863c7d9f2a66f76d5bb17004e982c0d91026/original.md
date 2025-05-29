```
fixed(args...)
```

Fix parameters to a certain value. For ensemble models, multiple values (one for each submodel/group) are needed.

# Examples

```julia
graph = @StenoGraph begin
    x → fixed(1)*y
end
```
