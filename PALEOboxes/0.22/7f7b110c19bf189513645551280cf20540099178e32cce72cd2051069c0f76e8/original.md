```
add_method_do_totals_default!(react::AbstractReaction, total_candidates=PB.get_variables(react);
    [filterfn] [, methodname] [, total_localnames] [, operatorID])
```

Create and add a method to add total variables (Scalar Properties), for Variables in collection `total_candidates` that match `filterfn` (defaults to those that are Array Variables and have attribute ``:calc_total == true`).

NB: total Variables will require initialization to zero using [`add_method_initialize_zero_vars_default!`](@ref)
