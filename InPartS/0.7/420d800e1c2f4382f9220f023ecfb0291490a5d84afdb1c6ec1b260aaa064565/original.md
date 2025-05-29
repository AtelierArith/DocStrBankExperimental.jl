```
@forcedef [function definition]
```

Function decorator for force extraction.

Function definitions decorated with `forcedef` are expanded into two methods, the latter of which contains an additional first positional argument `acc`, which can be used to accumulate values.

All expressions decorated with [`@force`](@ref) are pushed into the accumulator. The accumulator is added as the first positional argument to all function calls decorated with `@forcefun`

# Example

The function definition

```
@forcedef function examplefunction(x1; x2 = 0.1)
    dx = @forcefun otherfunction(x1 - x2)
    @force dx
    return dx^2
end
```

is expanded to

```
function examplefunction(x1; x2 = 0.1)
    dx = otherfunction(x1 - x2)
    return dx^2
end

function examplefunction(acc, x1; x2 = 0.1)
    dx = otherfunction(acc, x1 - x2)
    push!(acc, dx)
    return dx^2
end
```
