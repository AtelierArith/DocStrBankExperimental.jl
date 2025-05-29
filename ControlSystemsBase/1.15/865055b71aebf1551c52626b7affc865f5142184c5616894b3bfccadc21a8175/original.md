```
pidplots(P, args...; params_p, params_i, params_d=0, form=:standard, ω=0, grid=false, kwargs...)
```

Display the relevant plots related to closing the loop around process `P` with a PID controller supplied in `params` on one of the following forms:

  * `:standard` - `Kp*(1 + 1/(Ti*s) + Td*s)`
  * `:series` - `Kc*(1 + 1/(τi*s))*(τd*s + 1)`
  * `:parallel` - `Kp + Ki/s + Kd*s`

The sent in values can be arrays to evaluate multiple different controllers, and if `grid=true` it will be a grid search  over all possible combinations of the values.

Available plots are `:gof` for Gang of four, `:nyquist`, `:controller` for a bode plot of the controller TF and `:pz` for pole-zero maps and should be supplied as additional arguments to the function.

One can also supply a frequency vector `ω` to be used in Bode and Nyquist plots.

See also `loopshapingPI`, `stabregionPID`
