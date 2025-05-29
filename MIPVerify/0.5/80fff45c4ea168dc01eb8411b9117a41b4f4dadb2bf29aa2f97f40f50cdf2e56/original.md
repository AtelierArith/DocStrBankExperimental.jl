```julia
find_adversarial_example(
    nn,
    input,
    target_selection,
    optimizer,
    main_solve_options;
    invert_target_selection,
    pp,
    norm_order,
    adversarial_example_objective,
    tightening_algorithm,
    tightening_options,
    solve_if_predicted_in_targeted
)

```

Perturbs `input` such that the network `nn` classifies the perturbed image in one of the categories identified by the indexes in `target_selection`.

IMPORTANT: 

1. `target_selection` can include the correct label for `input`.
2. It is possible (particularly with the `closest` objective) to see 'ties' – that is, the perturbed input produces an output with two logits (one corresponding to a target category, and one corresponding to a non-target category) taking on the same maximal value. See the formal definition below for more; in particular, note that '≥' sign.

`optimizer` is used to build and solve the MIP problem.

The output dictionary has keys `:Model, :PerturbationFamily, :TargetIndexes, :SolveStatus, :Perturbation, :PerturbedInput, :Output`. See the [tutorial](https://nbviewer.jupyter.org/github/vtjeng/MIPVerify.jl/blob/master/examples/03_interpreting_the_output_of_find_adversarial_example.ipynb) on what individual dictionary entries correspond to.

*Formal Definition*: If there are a total of `n` categories, the (perturbed) output vector `y=d[:Output]=d[:PerturbedInput] |> nn` has length `n`. If `:SolveStatus` is feasible, we guarantee that `y[j] - y[i] ≥ 0` for some `j ∈ target_selection` and for all `i ∉ target_selection`.

# Keyword Arguments:

  * `invert_target_selection`: Defaults to `false`. If `true`, sets `target_selection` to be its   complement.
  * `pp`: Defaults to `UnrestrictedPerturbationFamily()`. Determines the search space for adversarial examples.
  * `norm_order`: Defaults to `1`. Determines the distance norm used to determine the distance from   the perturbed image to the original. Allowed options are `1` and `Inf`, and `2` if the   `optimizer` can solve MIQPs.
  * `adversarial_example_objective`: Defaults to `closest`. Allowed options are `closest` or `worst`.

      * `closest` finds the closest adversarial example, as measured by the `norm_order` norm.
      * `worst` finds the adversarial example with the *largest* gap between `max(y[j)` for `j ∈ target_selection` and `max(y[i])` for all `i ∉ target_selection`.
  * `tightening_algorithm`: Defaults to `mip`. Determines how we determine the upper and lower bounds   on input to each nonlinear unit. Allowed options are `interval_arithmetic`, `lp`, `mip`.

      * `interval_arithmetic` looks at the bounds on the output to the previous layer.
      * `lp` solves an `lp` corresponding to the `mip` formulation, but with any integer constraints relaxed.
      * `mip` solves the full `mip` formulation.
  * `tightening_options`: Solver-specific options passed to optimizer when used to determine upper   and lower bounds for input to nonlinear units. Note that these are only used if the   `tightening_algorithm` is `lp` or `mip` (no solver is used when `interval_arithmetic` is used   to compute the bounds). Defaults for Gurobi and HiGHS to a time limit of 20s per solve, with   output suppressed.
  * `solve_if_predicted_in_targeted`: Defaults to `true`. The prediction that `nn` makes for the   unperturbed `input` can be determined efficiently. If the predicted index is one of the indexes   in `target_selection`, we can skip the relatively costly process of building the model for the   MIP problem since we already have an "adversarial example" –- namely, the input itself. We   continue build the model and solve the (trivial) MIP problem if and only if   `solve_if_predicted_in_targeted` is `true`.
