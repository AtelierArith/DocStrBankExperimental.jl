```
KalmanFilter(A,B,C,D,R1,R2,d0=MvNormal(R1); p = NullParameters(), α=1, check=true)
```

The matrices `A,B,C,D` define the dynamics

```
x' = Ax + Bu + w
y  = Cx + Du + e
```

where `w ~ N(0, R1)`, `e ~ N(0, R2)` and `x(0) ~ d0`

The matrices can be time varying such that, e.g., `A[:, :, t]` contains the $A$ matrix at time index `t`. They can also be given as functions on the form

```
Afun(x, u, p, t) -> A
```

When providing functions, the dimensions of the state, input and output, `nx, nu, ny` must be provided as keyword arguments to the `KalmanFilter` constructor since these cannot be inferred from the function signature. For maximum performance, provide statically sized matrices from StaticArrays.jl

α is an optional "forgetting factor", if this is set to a value > 1, such as 1.01-1.2, the filter will, in addition to the covariance inflation due to $R_1$, exhibit "exponential forgetting" similar to a [Recursive Least-Squares (RLS) estimator](https://en.wikipedia.org/wiki/Recursive_least_squares_filter). It is thus possible to get a RLS-like algorithm by setting $R_1=0, R_2 = 1/α$ and $α > 1$ ($α$ is the inverse of the traditional RLS parameter $α = 1/λ$). The exact form of the covariance update is

$$
R(t+1|t) = α AR(t)A^T + R_1
$$

If `check = true (default)` the function will check that the eigenvalues of `A` are less than 2 in absolute value. Large eigenvalues may be an indication that the system matrices are representing a continuous-time system and the user has forgotten to discretize it. Turn off this check by setting `check = false`.

# Tutorials on Kalman filtering

The tutorial ["How to tune a Kalman filter"](https://juliahub.com/pluto/editor.html?id=ad9ecbf9-bf83-45e7-bbe8-d2e5194f2240) details how to figure out appropriate covariance matrices for the Kalman filter, as well as how to add disturbance models to the system model. See also the [tutorial in the documentation](https://baggepinnen.github.io/LowLevelParticleFilters.jl/stable/adaptive_kalmanfilter/)
