```
matchplot2
```

Like `matchplot`, but works with 2d and 3d signals.

### Inputs

#### Positional args

For available positional argument patterns, see `DynamicAxisWarping.handleargs`

Generally, it can accept a `x` and `y` signal to warp and optionally `dtw_cost_matrix` inputs, or `x` and `y` signal plus `dtw` or `dtw_cost_matrix` outputs (skipping the warp step).

#### Keyword args

  * `transportcost` – see `dtw_cost_matrix`
  * `separation` – extra separation/padding added between the signals in in ℜⁿ
  * `showindex` – Whether to add an axis in the plot for the index/"time" axis (appends to the last dimension)
