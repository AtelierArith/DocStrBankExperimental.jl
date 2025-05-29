Define one or more differentials.

# Examples

```jldoctest
julia> using Symbolics

julia> @variables x y z;

julia> Dx = Differential(x); Dy = Differential(y);  # Create differentials wrt. x and y

julia> Dx(z)  # Differentiate z wrt. x
Differential(x)(z)

julia> Dy(z)  # Differentiate z wrt. y
Differential(y)(z)
```
