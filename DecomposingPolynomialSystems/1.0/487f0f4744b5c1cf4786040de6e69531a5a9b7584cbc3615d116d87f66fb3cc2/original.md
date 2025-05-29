```
symmetries_fixing_parameters(F::System; degree_bound=1, param_dep=true, kwargs...)
```

Given a polynomial system F returns the group of symmetries  of `F` that fix the parameters. The keyword argument `degree_bound` is used to set the upper bound for the degrees of numerator and denominator polynomials in expressions for the symmetries. The `param_dep` keyword argument specifies whether to consider functions of the symmetries to be dependent on the parameters of `F`.

```julia-repl
julia> @var x[1:2] p[1:2];

julia> F = System([x[1]^2 - x[2]^2 - p[1], 2*x[1]*x[2] - p[2]]; variables=x, parameters=p);

julia> symmetries_fixing_parameters(F; degree_bound=1, param_dep=false)
DeckTransformationGroup of order 4
 structure: C2 x C2
 action:
  1st map:
   x₁ ↦ x₁
   x₂ ↦ x₂
  2nd map:
   x₁ ↦ -x₁
   x₂ ↦ -x₂
  3rd map:
   x₁ ↦ im*x₂
   x₂ ↦ -im*x₁
  4th map:
   x₁ ↦ -im*x₂
   x₂ ↦ im*x₁
```
