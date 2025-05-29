```
EndgameOptions(; options...)
```

Options controlling the behaviour of a [`EndgameTracker`](@ref).

## Options

  * `at_infinity_check = true`: Whether divering paths should be truncated.
  * `endgame_start = 0.1`: The point `t` in time where the endgame starts. Set it to `0.0` to disable the endgame.
  * `only_nonsingular = false`: If `true` don't run the Cauchy endgame to handle singular solutions.
  * `zero_is_at_infinity = false`: Whether paths going to a solution where at least one coordinates is zero should also be considered diverging.

### Parameters

These parameters control the behaviour during the endgame.

  * `max_endgame_steps = 2000`: The maximal number of steps performed during the endgame.
  * `max_winding_number = 6`: The maximal winding number which is attempted in the Cauchy endgame.
  * `min_cond = 1e6`: The minimal condition number after which an endgame strategy is considered to be applied.
  * `min_cond_growth = 1e4`: The minimal condition number growth after which an  endgame strategy is considered to be applied.
  * `min_coord_growth = 100`: The minimal relative growth of a coordinate necessary to to be considered going to infininity (resp. zero).
  * `val_at_infinity_tol = 1e-3`: Tolerance on the valuation which has to be satisfied before a path is considered to diverge / go to infinity.
  * `val_finite_tol = 1e-3`: Tolerance on the valuation which has to be satisfied before the endgame is started.
  * `sing_cond = 1e14`: value for the condition number above which a solution is considered singular.
  * `sing_accuracy = 1e-12`: value for the accuracy number above which a solution is considered singular.
  * `refine_steps = 3`: number of steps for refining solutions at the end.
