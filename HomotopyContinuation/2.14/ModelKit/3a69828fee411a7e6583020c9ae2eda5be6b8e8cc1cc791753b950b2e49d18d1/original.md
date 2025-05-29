```
subs(expr::Expression, subsitutions::Pair...)
subs(exprs::AbstractVector{<:Expression}, subsitutions::Pair...)
```

Apply the given substitutions to the given expressions.

## Examples

```julia-repl
@var x y

julia> subs(x^2, x => y)
y ^ 2

julia> subs(x * y, [x,y] => [x+2,y+2])
(x + 2) * (y + 2)

julia> subs([x + y, x^2], x => y + 2, y => x + 2)
2-element Array{Expression,1}:
 4 + x + y
 (2 + y)^2

# You can also use the callable syntax
julia> (x * y)([x,y] => [x+2,y+2])
 (x + 2) * (y + 2)
```
