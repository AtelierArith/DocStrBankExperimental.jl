```
K, γ, mats = hinfsynthesize(P::ExtendedStateSpace; gtol = 1e-4, interval = (0, 20), verbose = false, tolerance = 1.0e-10, γrel = 1.01, transform = true, ftype = Float64, check = true)
```

Computes an H-infinity optimal controller `K` for an extended plant `P` such that $||F_l(P, K)||∞ < γ$(`lft(P, K)`) for the smallest possible γ given `P`. The routine is known as the γ-iteration, and is based on the paper "State-space formulae for all stabilizing controllers that satisfy an H∞-norm bound and relations to risk sensitivity" by Glover and Doyle.

# Arguments:

  * `gtol`: Tolerance for γ.
  * `interval`: The starting interval for the bisection.
  * `verbose`: Print progress?
  * `tolerance`: For detecting eigenvalues on the imaginary axis.
  * `γrel`: If `γrel > 1`, the optimal γ will be found by γ iteration after which a controller will be designed for `γ = γopt * γrel`. It is often a good idea to design a slightly suboptimal controller, both for numerical reasons, but also since the optimal controller may contain very fast dynamics. If `γrel → ∞`, the computed controller will approach the 𝑯₂ optimal controller. Getting a mix between 𝑯∞ and 𝑯₂ properties is another reason to choose `γrel > 1`.
  * `transform`: Apply coordiante transform in order to tolerate a wider range or problem specifications.
  * `ftype`: construct problem matrices in higher precision for increased numerical robustness. If the calculated controller achieves
  * `check`: Perform a post-design check of the γ value achieved by the calculated controller. A warning is issued if the achieved γ differs from the γ calculated during design. If this warning is issued, consider using a higher-precision number type like `ftype = BigFloat`.

See the example folder for example usage.
