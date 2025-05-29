```julia
DiffEqBase.NonlinearProblem(rs::ReactionSystem, u0,
        p = DiffEqBase.NullParameters(), args...;
        name = nameof(rs), combinatoric_ratelaws = get_combinatoric_ratelaws(rs),
        remove_conserved = false, checks = false, check_length = false, 
        structural_simplify = remove_conserved, all_differentials_permitted = false, 
        kwargs...)
```

Convert a [`ReactionSystem`](@ref) to an `ModelingToolkit.NonlinearSystem`.

Keyword args and default values:

  * `combinatoric_ratelaws=true` uses factorial scaling factors in calculating the rate law, i.e. for `2S -> 0` at rate `k` the ratelaw would be `k*S^2/2!`. Set `combinatoric_ratelaws=false` for a ratelaw of `k*S^2`, i.e. the scaling factor is ignored. Defaults to the value given when the `ReactionSystem` was constructed (which itself defaults to true).
  * `remove_conserved=false`, if set to `true` will calculate conservation laws of the underlying set of reactions (ignoring coupled ODE or algebraic equations). For each conservation law one steady-state equation is eliminated, and replaced with the conservation law. This ensures a non-singular Jacobian. When using this option, it is recommended to call `ModelingToolkit.structural_simplify` on the converted system to then eliminate the conservation laws from the system equations.
  * `conseqs_remake_warn = true`, set to false to disable warning about `remake` and conservation laws. See the [FAQ entry](https://docs.sciml.ai/Catalyst/stable/faqs/#faq_remake_nonlinprob) for more details.
  * `expand_catalyst_funs = true`, replaces Catalyst defined functions like `hill(A,B,C,D)` with their rational function representation when converting to another system type. Set to `false`` to disable.
