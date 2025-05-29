```
plot_a_solution(
  dir::String,
  feop::ParamOperator,
  sol::AbstractSnapshots,
  sol_approx::AbstractSnapshots,
  args...;
  kwargs...
  ) -> Nothing
```

Plots a single FE solution, RB solution, and the point-wise error between the two, by selecting the first FE snapshot in `sol` and the first reduced snapshot in `sol_approx`
