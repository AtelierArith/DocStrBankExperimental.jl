```
evaluate(expr::Expression, subs...)
evaluate(expr::AbstractArray{Expression}, subs...)
```

Evaluate the given expression.

## Example

```julia-repl
julia> @var x y;

julia> evaluate(x^2, x => 2)
4

julia> evaluate(x * y, [x,y] => [2, 3])
6

julia> evaluate([x^2, x * y], [x,y] => [2, 3])
2-element Array{Int64,1}:
 4
 6

# You can also use the callable syntax
julia> [x^2, x * y]([x,y] => [2, 3])
2-element Array{Int64,1}:
 4
 6
```
