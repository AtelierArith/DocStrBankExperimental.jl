```
Smoothing(transition::Float64=0.0, gain::Float64=1.0)
```

Parameters to smooth calculations involving discontinuities (step functions).

Default values which disable smoothing are available as the `NoSmoothing` const.

## Background and purpose

Several computations like operating hours, fuel consumption... involve a step function which is discontinuous at zero:

step(x) = 0.0 if x==0.0 and 1.0 if 0 < x ≤ 1.0

This step can be smoothed linearly for 0 ≤ x ≤ `transition`. The `transition` parameter should be between:

  * 0.0:no smoothing (default value)
  * 1.0: strongest smoothing (i.e. convex relaxation)

Smoothing is recommended when using gradient-based optimization and then a “small enough” `transition` value between 0.05 and 0.30 is suggested.

Also, because this smoothing underestimates the true step, an optional `gain`≥1, can be applied, so that step(x) = gain for x ≥ `transition`.
