Replaces an expression with `lift(argtuple -> expression, args...)`, where `args` are all expressions inside the main one that begin with $.

# Example:

```julia
x = Observable(rand(100))
y = Observable(rand(100))
```

## before

```julia
z = lift((x, y) -> x .+ y, x, y)
```

## after

```julia
z = @lift($x .+ $y)
```

You can also use parentheses around an expression if that expression evaluates to an observable.

```julia
nt = (x = Observable(1), y = Observable(2))
@lift($(nt.x) + $(nt.y))
```
