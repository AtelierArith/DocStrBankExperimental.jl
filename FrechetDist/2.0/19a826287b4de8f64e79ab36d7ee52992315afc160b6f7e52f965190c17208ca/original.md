```
frechet_c_approx
```

Approximates the continuous Frechet distance between the two input curves. Returns a monotone morphing realizing it.

# Arguments

  * `approx` : The output morhing has Frechet distance <= approx*optimal.

Importantly, approx can be larger than 2, if you want a rough approximation.

The quality of approximation is available at ret.ratio. Thus, ret.leash/ret.ratio is a lower bound on the Frechet distance, while ret.leash is an upper bound.
