```
@alias name
```

Create a parameter alias. Use `@alias` in the [`@parameters`](@ref) section of your model definition.

```
@parameters model begin
    a = 5
    b = @alias a
end
```
