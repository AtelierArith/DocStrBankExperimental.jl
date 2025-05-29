```
test_rrule([config::RuleConfig,] f, args...; kwargs...)
```

# Arguments

  * `config`: defaults to `ChainRulesTestUtils.TestConfig`.
  * `f`: function for which the `rrule` should be tested. Its tangent can be provided using `f ⊢ f̄`. (You can enter `⊢` via `\vdash` + tab in the Julia REPL and supporting editors.)
  * `args...`: either the primal args `x`, or primals and their tangents: `x ⊢ x̄`

      * `x`: input at which to evaluate `f` (should generally be set to an arbitrary point in the domain).
      * `x̄`: currently accumulated cotangent; will be generated automatically if not provided.

    Non-differentiable arguments, such as indices, should have `x̄` set as `NoTangent()`.

# Keyword Arguments

  * `output_tangent`: the seed to propagate backward for testing (technically a cotangent). should be a differential for the output of `f`. Is set automatically if not provided.
  * `check_thunked_output_tangent=true`: also checks that passing a thunked version of the   output tangent to the pullback returns the same result.
  * `fdm::FiniteDifferenceMethod`: the finite differencing method to use.
  * `rrule_f=rrule`: function with an `rrule`-like API that is tested (defaults to `rrule`). Used for testing gradients from AD systems.
  * If `check_inferred=true`, then the inferrability (type-stability) of the `rrule` is checked — if `f` is itself inferrable — along with the inferrability of the pullback it returns.
  * `fkwargs` are passed to `f` as keyword arguments.
  * `testset_name`: if provided, the name of the testset used to wrap the tests.

Otherwise it is determined from the function and argument types.

  * All remaining keyword arguments are passed to `isapprox`.
