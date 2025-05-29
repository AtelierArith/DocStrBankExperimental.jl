```
FixedPointAccelerationJL(;
    algorithm = :Anderson, m = missing, condition_number_threshold = missing,
    extrapolation_period = missing, replace_invalids = :NoAction
)
```

Wrapper over [FixedPointAcceleration.jl](https://s-baumann.github.io/FixedPointAcceleration.jl/) for solving Fixed Point Problems. We allow using this algorithm to solve root finding problems as well.

### Keyword Arguments

  * `algorithm`: The algorithm to use. Can be `:Anderson`, `:MPE`, `:RRE`, `:VEA`, `:SEA`, `:Simple`, `:Aitken` or `:Newton`.
  * `m`: The number of previous iterates to use for the extrapolation. Only valid for `:Anderson`.
  * `condition_number_threshold`: The condition number threshold for Least Squares Problem. Only valid for `:Anderson`.
  * `extrapolation_period`: The number of iterates between extrapolations. Only valid for `:MPE`, `:RRE`, `:VEA` and `:SEA`. Defaults to `7` for `:MPE` & `:RRE`, and `6` for `:SEA` and `:VEA`. For `:SEA` and `:VEA`, this must be a multiple of `2`.
  * `replace_invalids`: The method to use for replacing invalid iterates. Can be `:ReplaceInvalids`, `:ReplaceVector` or `:NoAction`.

!!! note
    This algorithm is only available if `FixedPointAcceleration.jl` is installed and loaded.

