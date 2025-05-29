Replaces an expression with lift(argtuple -> expression, args...), where args are all expressions inside the main one that begin with $.

# Example:

x = Node(rand(100)) y = Node(rand(100))

## before

z = lift((x, y) -> x .+ y, x, y)

## after

z = @lift(:x .+ :y)

You can also use parentheses around an expression if that expression evaluates to a node.

```julia
nt = (x = Node(1), y = Node(2))
@lift($(nt.x) + $(nt.y))
```
