```
GeodesicAcceleration(; descent, finite_diff_step_geodesic, α)
```

Uses the `descent` algorithm to compute the velocity and acceleration terms for the geodesic acceleration method. The velocity and acceleration terms are then combined to compute the descent direction.

This method in its current form was developed for `LevenbergMarquardt`. Performance for other methods are not theorectically or experimentally verified.

### Keyword Arguments

  * `descent`: the descent algorithm to use for computing the velocity and acceleration.
  * `finite_diff_step_geodesic`: the step size used for finite differencing used to calculate the geodesic acceleration. Defaults to `0.1` which means that the step size is approximately 10% of the first-order step. See Section 3 of [1].
  * `α`: a factor that determines if a step is accepted or rejected. To incorporate geodesic acceleration as an addition to the Levenberg-Marquardt algorithm, it is necessary that acceptable steps meet the condition $\frac{2||a||}{||v||} \le \alpha_{\text{geodesic}}$, where $a$ is the geodesic acceleration, $v$ is the Levenberg-Marquardt algorithm's step (velocity along a geodesic path) and `α_geodesic` is some number of order `1`. For most problems `α_geodesic = 0.75` is a good value but for problems where convergence is difficult `α_geodesic = 0.1` is an effective choice. Defaults to `0.75`. See Section 3 of [transtrum2012improvements](@citet).
