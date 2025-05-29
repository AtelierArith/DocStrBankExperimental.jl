```
variables(expr::Expression; parameters = Variable[])
variables(exprs::AbstractVector{Expression}; parameters = Variable[])
```

Obtain all variables used in the given expression up to the ones declared in `parameters`.

## Example

```julia-repl
julia> @var x y a;
julia> variables(x^2 + y)
2-element Array{Variable,1}:
 x
 y

julia> variables([x^2 + a, y]; parameters = [a])
2-element Array{Variable,1}:
 x
 y
```
