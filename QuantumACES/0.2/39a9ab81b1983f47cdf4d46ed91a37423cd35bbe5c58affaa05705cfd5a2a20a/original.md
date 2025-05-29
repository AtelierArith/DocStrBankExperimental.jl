```
get_randomisations(d::Design, min_randomisations::Integer, target_shot_budget::Integer, experiment_shots::Integer; p_norm::Real = 2)
```

Returns the number of randomisations for each tuple in the experimental design `d`, given a target shot budget `target_shot_budget`, number of shots for each experiment `experiment_shots`, and minimum number of randomisations `min_randomisations`. The number of randomisations is greedily optimised to minimise the `p_norm`-norm to the shot weights associated with the experimental design.

Typically, the 2-norm works better for smaller shot budgets, and the 1-norm works better for larger shot budgets. The number of randomisations corresponds to unnormalised shot weights `randomisations .* d.experiment_numbers`.
