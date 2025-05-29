```
Homotopy(exprs, vars, t, parameters = Variable[])
```

Create a homotopy `H(vars,t)` from the given [`Expression`](@ref)s `exprs` where `vars` are the given variables and `t` is the dedicated variable parameterizing the family of systems. The `parameters` argument allows to declare certain [`Variable`](@ref)s as parameters.

## Example

```julia-repl
julia> @var x y t;

julia> H = Homotopy([x + t, y + 2t], [y, x], t)
Homotopy in t of length 2
 2 variables: y, x

 t + x
 2*t + y

julia> H([2, 3], 0)
2-element Array{Int64,1}:
 3
 2


julia> H([2, 3], 1)
2-element Array{Int64,1}:
 4
 4
```

It is also possible to declare additional variables.

```julia-repl
julia> @var x y t a b;
julia> H = Homotopy([x^2 + t*a, y^2 + t*b], [x, y], t, [a, b])
Homotopy in t of length 2
 2 variables: x, y
 2 parameters: a, b

 a*t + x^2
 b*t + y^2
julia> H([2, 3], 1, [5, 2])
2-element Array{Int64,1}:
 9
 11
```
