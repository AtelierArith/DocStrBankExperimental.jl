```
System(exprs::AbstractVector{Expression};
            variables = variables(exprssion),
            parameters = Variable[])
```

Create a system from the given [`Expression`](@ref)s `exprs`. The `variables` determine also the variable ordering. The `parameters` argument allows to declare certain [`Variable`](@ref)s as parameters.

```
System(support::AbstractVector{<:AbstractMatrix{<:Integer}},
       coefficients::AbstractVector{<:AbstractVector};
       variables,
       parameters = Variable[])
```

Create a system from the given support and coefficients.

## Examples

```julia-repl
julia> @var x y;
julia> F = System([x^2, y^2]; variables = [y, x])
System of length 2
 2 variables: y, x

 x^2
 y^2

# Systems are callable.
# This evaluates F at y=2 and x=3
julia> F([2, 3])
2-element Array{Int64,1}:
 9
 4
```

It is also possible to declare parameters.

```julia-repl
julia> @var x y a b;
julia> F = System([x^2 + a, y^2 + b]; variables = [y, x], parameters = [a, b])
System of length 2
 2 variables: y, x
 2 parameters: a, b

 a + x^2
 b + y^2

julia> F([2, 3], [5, -2])
 2-element Array{Int64,1}:
  14
   2
```
