```julia
batch_find_untargeted_attack(
    nn,
    dataset,
    target_indices,
    optimizer,
    main_solve_options;
    save_path,
    solve_rerun_option,
    pp,
    norm_order,
    tightening_algorithm,
    tightening_options,
    solve_if_predicted_in_targeted,
    adversarial_example_objective
)

```

Runs [`find_adversarial_example`](@ref) for the specified neural network `nn` and `dataset` for samples identified by the `target_indices`, with the target labels for each sample set to the complement of the true label.

It creates a named directory in `save_path`, with the name summarizing

1. the name of the network in `nn`,
2. the perturbation family `pp`,
3. the `norm_order`

Within this directory, a summary of all the results is stored in `summary.csv`, and results from individual runs are stored in the subfolder `run_results`.

This functioned is designed so that it can be interrupted and restarted cleanly; it relies on the `summary.csv` file to determine what the results of previous runs are (so modifying this file manually can lead to unexpected behavior.)

If the summary file already contains a result for a given target index, the `solve_rerun_option` determines whether we rerun [`find_adversarial_example`](@ref) for this particular index.

`optimizer` specifies the optimizer used to solve the MIP problem once it has been built and `main_solve_options` specifies the options that will be passed to the optimizer for the  main solve.

# Named Arguments:

  * `save_path`: Directory where results will be saved. Defaults to current directory.
  * `pp, norm_order, tightening_algorithm, tightening_options, solve_if_predicted_in_targeted` are passed through to [`find_adversarial_example`](@ref) and have the same default values; see documentation for that function for more details.
  * `solve_rerun_option::MIPVerify.SolveRerunOption`: Options are `never`, `always`, `resolve_ambiguous_cases`, and `refine_insecure_cases`. See [`run_on_sample_for_untargeted_attack`](@ref) for more details.
