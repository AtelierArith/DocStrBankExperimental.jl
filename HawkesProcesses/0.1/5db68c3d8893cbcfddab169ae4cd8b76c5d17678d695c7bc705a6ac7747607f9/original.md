```
simulate(bg::Number, kappa::Float64, kern::Function, maxT::Number)
```

Simulate a Hawkes process between 0 and `maxT` with parameters `bg`, `kappa`, `kern`.

# Arguments

  * `bg`: The background rate of the Hawkes process. Constant or positive function.
  * `kappa`: The kappa parameter of the Hawkes process.
  * `kern` : The kernel function of the Hawkes process.
  * `maxT` : Maximum time that the Hawkes process will be simulated for.

# Notes

  * kappa must be between 0 and 1 for a stable Hawkes process.

# Examples

``julia kern_f(x) = pdf.(Distributions.Exponential(1/0.5), x)

simevents = simulate(0.5, 0.5, kern_f, 100) ``
