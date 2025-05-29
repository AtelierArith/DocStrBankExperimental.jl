```julia
struct NLS_ForwardDiff <: AbstractNLS
    ...
end

```

A specialization that uses the `ForwardDiff` package to compute the Jacobian.

By comparison with [`AbstractNLS`](@ref) you only have to define these functions:

  * [`parameter_size`](@ref) : returns $n_θ$
  * [`residue_size`](@ref) : returns $n_S$
  * [`eval_r`](@ref) : computation of $\mathbf{r}$

See: [`create_NLS_problem_using_ForwardDiff`](@ref) 
