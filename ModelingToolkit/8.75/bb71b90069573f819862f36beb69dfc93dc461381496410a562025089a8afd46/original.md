```julia
structural_simplify(sys; ...)
structural_simplify(sys, io; simplify, kwargs...)

```

Structurally simplify algebraic equations in a system and compute the topological sort of the observed equations. When `simplify=true`, the `simplify` function will be applied during the tearing process. It also takes kwargs `allow_symbolic=false` and `allow_parameter=true` which limits the coefficient types during tearing.

The optional argument `io` may take a tuple `(inputs, outputs)`. This will convert all `inputs` to parameters and allow them to be unconnected, i.e., simplification will allow models where `n_states = n_equations - n_inputs`.
