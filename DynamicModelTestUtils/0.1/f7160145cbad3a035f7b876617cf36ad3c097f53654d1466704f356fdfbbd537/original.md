```
compare(
    new_sol::SciMLBase.AbstractTimeseriesSolution,
    reference::DataFrame,
    cmp=DefaultComparison(); to_name=string, warn_observed=true)
```

`compare` compares the results of `new_sol` to a result in `reference`, which may come from either experiment or a previous model execution. The format of `reference` is that produced by [`discretize_solution`](@ref):

  * A column named "timestamp" that indicates the time the measurement was taken (referenced to the same timebase as the solution provided)
  * Columns with names matching the names in the completed system `new_sol` (fully qualified)

If `new_sol` is dense then the discretization nodes don't need to line up with the `reference` and the interpolant will be used instead. If it is not dense then the user must ensure that the saved states in are at the same times as the "timestamp"s are in the reference data.

`compare` will use the comparison method specified by `cmp` to compare the two solutions; by default it uses the [`DefaultComparison`](@ref) (which offers l1, l2, and rms comparisons per observed value), but you can pass your own. Look at `DefaultComparison` for more details on how.

The two optional named parameters are `to_name` (which is used to convert the symbolic variables in `new_sol` into valid column names for  the dataframe) and `warn_observed` which controls whether `compare` complains about comparing observed values to non-observed values. We suggest leaving `warn_observed` on for regression testing (it'll give you a note when MTK changes the simplifcation of the system).
