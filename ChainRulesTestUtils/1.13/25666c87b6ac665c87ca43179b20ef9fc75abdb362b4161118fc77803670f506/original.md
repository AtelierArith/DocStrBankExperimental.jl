```
test_frule([config::RuleConfig,] f, args..; kwargs...)
```

# Arguments

  * `config`: defaults to `ChainRulesTestUtils.TestConfig`.
  * `f`: function for which the `frule` should be tested. Its tangent can be provided using `f ⊢ ḟ`. (You can enter `⊢` via `\vdash` + tab in the Julia REPL and supporting editors.)
  * `args...`: either the primal args `x`, or primals and their tangents: `x ⊢ ẋ`

      * `x`: input at which to evaluate `f` (should generally be set to an arbitrary point in the domain).
      * `ẋ`: differential w.r.t. `x`; will be generated automatically if not provided.

    Non-differentiable arguments, such as indices, should have `ẋ` set as `NoTangent()`.

# Keyword Arguments

  * `output_tangent`: tangent against which to test accumulation of derivatives. Should be a differential for the output of `f`. Is set automatically if not provided.
  * `fdm::FiniteDifferenceMethod`: the finite differencing method to use.
  * `frule_f=frule`: function with an `frule`-like API that is tested (defaults to `frule`). Used for testing gradients from AD systems.
  * If `check_inferred=true`, then the inferrability (type-stability) of the `frule` is checked, as long as `f` is itself inferrable.
  * `fkwargs` are passed to `f` as keyword arguments.
  * `testset_name`: if provided, the name of the testset used to wrap the tests.

Otherwise it is determined from the function and argument types.

  * All remaining keyword arguments are passed to `isapprox`.
