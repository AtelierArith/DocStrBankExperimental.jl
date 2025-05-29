```
kalman(Continuous, A, C, R1, R2)
kalman(Discrete, A, C, R1, R2; direct = false)
kalman(sys, R1, R2; direct = false)
```

Calculate the optimal asymptotic Kalman gain for the linear-Gaussian model

$$
\begin{aligned}
dx &= Ax + Bu + w \\
y &= Cx + v
\end{aligned}
$$

where `w` is the dynamics noise with covariance `R1` and `v` is the measurement noise with covariance `R2`.

If `direct = true`, the observer gain is computed for the pair `(A, CA)` instead of `(A,C)`. This option is intended to be used together with the option `direct = true` to [`observer_controller`](@ref). Ref: "Computer-Controlled Systems" pp 140. `direct = false` is sometimes referred to as a "delayed" estimator, while `direct = true` is a "current" estimator.

To obtain a discrete-time approximation to a continuous-time LQG problem, the function [`c2d`](@ref) can be used to obtain corresponding discrete-time covariance matrices.

To obtain an LTISystem that represents the Kalman filter, pass the obtained Kalman feedback gain into [`observer_filter`](@ref). To obtain an LQG controller, pass the obtained Kalman feedback gain as well as a state-feedback gain computed using [`lqr`](@ref) into [`observer_controller`](@ref).

The `args...; kwargs...` are sent to the Riccati solver, allowing specification of cross-covariance etc. See `?MatrixEquations.arec/ared` for more help.

# FAQ

This function requires

  * `R1` must be positive semi-definite
  * `R2` must be positive definite
  * The pair `(A,R1)` must not have any uncontrollable modes on the imaginary axis (cont) / unit circle (disc), e.g., there must not be any integrating modes that are not affected through `R1`. if this condition does not hold, you may get the error "The Hamiltonian matrix is not dichotomic".
