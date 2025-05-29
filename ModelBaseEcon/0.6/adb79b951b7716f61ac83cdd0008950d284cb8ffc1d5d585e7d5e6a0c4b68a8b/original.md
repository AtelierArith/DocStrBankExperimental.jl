```
@link expr
```

Create a parameter link. Use `@link` in the [`@parameters`](@ref) section of your model definition.

If your parameter depends on other parameters, then you use `@link` to declare that. The expression can be any valid Julia code.

```
@parameters model begin
    a = 5
    b = @link a + 1
end
```

When a parameter the link depends on is assigned a new value, the link that depends on it gets updated automatically.

!!! note "Important note"
    There are two cases in which the value of a link does not get updated automatically. If the parameter it depends on is mutable, e.g. a `Vector`, it is possible for it to get updated in place. The other case is when the link contains global variable or custom function.

    In such case, it is necessary to call [`update_links!`](@ref).

