```julia
struct Differential <: Symbolics.Operator
```

Represents a differential operator.

# Fields

  * `x`: The variable or expression to differentiate with respect to.

# Examples

```jldoctest
julia> using Symbolics

julia> @variables x y;

julia> D = Differential(x)
(D'~x)

julia> D(y) # Differentiate y wrt. x
(D'~x)(y)

julia> Dx = Differential(x) * Differential(y) # d^2/dxy operator
(D'~x(t)) ∘ (D'~y(t))

julia> D3 = Differential(x)^3 # 3rd order differential operator
(D'~x(t)) ∘ (D'~x(t)) ∘ (D'~x(t))
```
