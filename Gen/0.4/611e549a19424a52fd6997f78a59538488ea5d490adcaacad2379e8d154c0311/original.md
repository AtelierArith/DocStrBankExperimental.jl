```
(new_trace, accepted) = metropolis_hastings(
    trace, proposal::GenerativeFunction, proposal_args::Tuple,
    involution::Union{TraceTransformDSLProgram,Function};
    check=false, observations=EmptyChoiceMap())
```

Perform a generalized (reversible jump) Metropolis-Hastings update based on an involution (bijection that is its own inverse) on a space of choice maps, returning the new trace (which is equal to the previous trace if the move was not accepted) and a Bool indicating whether the move was accepted or not.

Most users will want to construct `involution` using the [Trace Transform DSL](@ref) with the [`@transform`](@ref) macro, but for more user control it is also possible to provide a Julia function for `involution`, that has the following signature:

```
(new_trace, bwd_choices::ChoiceMap, weight) = involution(trace::Trace, fwd_choices::ChoiceMap, fwd_retval, fwd_args::Tuple)
```

The generative function `proposal` is executed on arguments `(trace, proposal_args...)`, producing a choice map `fwd_choices` and return value `fwd_ret`. For each value of model arguments (contained in `trace`) and `proposal_args`, the `involution` function applies an involution that maps the tuple `(get_choices(trace), fwd_choices)` to the tuple `(get_choices(new_trace), bwd_choices)`. Note that `fwd_ret` is a deterministic function of `fwd_choices` and `proposal_args`. When only discrete random choices are used, the `weight` must be equal to `get_score(new_trace) - get_score(trace)`.

When continuous random choices are used, the `weight` returned by the involution must include an additive correction term that is the determinant of the the Jacobian of the bijection on the continuous random choices that is obtained by currying the involution on the discrete random choices (this correction term is automatically computed if the involution is constructed using the [Trace Transform DSL](@ref)). NOTE: The Jacobian matrix of the bijection on the continuous random choices must be full-rank (i.e. nonzero determinant). The `check` keyword argument to the involution can be used to enable or disable any dynamic correctness checks that the involution performs; for successful executions, `check` does not alter the return value.
