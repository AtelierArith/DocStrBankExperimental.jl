```julia
structural_simplify(sys; ...)
structural_simplify(
    sys,
    io;
    additional_passes,
    simplify,
    split,
    allow_symbolic,
    allow_parameter,
    conservative,
    fully_determined,
    kwargs...
)

```

Structurally simplify algebraic equations in a system and compute the topological sort of the observed equations in `sys`.

### Optional Arguments:

  * optional argument `io` may take a tuple `(inputs, outputs)`. This will convert all `inputs` to parameters and allow them to be unconnected, i.e., simplification will allow models where `n_unknowns = n_equations - n_inputs`.

### Optional Keyword Arguments:

  * When `simplify=true`, the `simplify` function will be applied during the tearing process.
  * `allow_symbolic=false`, `allow_parameter=true`, and `conservative=false` limit the coefficient types during tearing. In particular, `conservative=true` limits tearing to only solve for trivial linear systems where the coefficient has the absolute value of $1$.
  * `fully_determined=true` controls whether or not an error will be thrown if the number of equations don't match the number of inputs, outputs, and equations.
  * `sort_eqs=true` controls whether equations are sorted lexicographically before simplification or not.
