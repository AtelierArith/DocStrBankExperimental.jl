```
UnscentedKalmanFilter(dynamics, measurement, R1, R2, d0=MvNormal(Matrix(R1)); p = NullParameters(), ny, nu, weight_params)
UnscentedKalmanFilter{IPD,IPM,AUGD,AUGM}(dynamics, measurement_model::AbstractMeasurementModel, R1, d0=SimpleMvNormal(R1); p=NullParameters(), nu, weight_params)
```

A nonlinear state estimator propagating uncertainty using the unscented transform.

The dynamics and measurement function are on *either* of the following forms

```
x' = dynamics(x, u, p, t) + w
y  = measurement(x, u, p, t) + e
```

```
x' = dynamics(x, u, p, t, w)
y  = measurement(x, u, p, t, e)
```

where `w ~ N(0, R1)`, `e ~ N(0, R2)` and `x(0) ~ d0`. The former (default) assums that the noise is additive and added *after* the dynamics and measurement updates, while the latter assumes that the dynamics functions take an additional argument corresponding to the noise term. The latter form (sometimes refered to as the "augmented" form) is useful when the noise is multiplicative or when the noise is added *before* the dynamics and measurement updates. See "Augmented UKF" below for more details on how to use this form. In both cases should the noise be modeled as discrete-time white noise, see Discretization: [Covariance matrices](@ref).

The matrices `R1, R2` can be time varying such that, e.g., `R1[:, :, t]` contains the $R_1$ matrix at time index `t`. They can also be given as functions on the form

```
Rfun(x, u, p, t) -> R
```

For maximum performance, provide statically sized matrices from StaticArrays.jl

`ny, nu` indicate the number of outputs and inputs.

# Custom type of `u`

The input `u` may be of any type, e.g., a named tuple or a custom struct. The `u` provided in the input data is passed directly to the dynamics and measurement functions, so as long as the type is compatible with the dynamics it will work out. The one exception where this will not work is when calling `simulate`, which assumes that `u` is an array.

# Augmented UKF

If the noise is not additive, one may use the augmented form of the UKF. In this form, the dynamics functions take additional input arguments that correspond to the noise terms. To enable this form, the typed constructor

```
UnscentedKalmanFilter{inplace_dynamics,inplace_measurement,augmented_dynamics,augmented_measurement}(...)
```

is used, where the Boolean type parameters have the following meaning

  * `inplace_dynamics`: If `true`, the dynamics function operates in-place, i.e., it modifies the first argument in `dynamics(dx, x, u, p, t)`. Default is `false`.
  * `inplace_measurement`: If `true`, the measurement function operates in-place, i.e., it modifies the first argument in `measurement(y, x, u, p, t)`. Default is `false`.
  * `augmented_dynamics`: If `true` the dynamics function is augmented with an additional noise input `w`, i.e., `dynamics(x, u, p, t, w)`. Default is `false`.
  * `augmented_measurement`: If `true` the measurement function is agumented with an additional noise input `e`, i.e., `measurement(x, u, p, t, e)`. Default is `false`. (If the measurement noise has fewer degrees of freedom than the number of measurements, you may failure in Cholesky factorizations, see "Custom Cholesky factorization" below).

Use of augmented dynamics incurs extra computational cost. The number of sigma points used is `2L+1` where `L` is the length of the augmented state vector. Without augmentation, `L = nx`, with augmentation `L = nx + nw` and `L = nx + ne` for dynamics and measurement, respectively.

# Weight tuning

The spread of the sigma points is controlled by `weight_params::UTParams`. See [Docs: Unscented transform](https://baggepinnen.github.io/LowLevelParticleFilters.jl/dev/ut/) for a tutorial. The default is [`TrivialParams`](@ref) for unweighted sigma points, other options are [`WikiParams`](@ref) and [`MerweParams`](@ref).

# Sigma-point rejection

For problems with challenging dynamics, a mechanism for rejection of sigma points after the dynamics update is provided. A function `reject(x) -> Bool` can be provided through the keyword argument `reject` that returns `true` if a sigma point for $x(t+1)$ should be rejected, e.g., if an instability or non-finite number is detected. A rejected point is replaced by the propagated mean point (the mean point cannot be rejected). This function may be provided either to the constructor of the UKF or passed to the [`predict!`](@ref) function.

# Custom measurement models

By default, standard arithmetic mean and `e(y, yh) = y - yh` are used as mean and innovation functions.

By passing and explicitly created [`UKFMeasurementModel`](@ref), one may provide custom functions that compute the mean, the covariance and the innovation. This is useful in situations where the state or a measurement lives on a manifold. One may further override the mean and covariance functions for the state sigma points by passing the keyword arguments `state_mean` and `state_cov` to the constructor.

  * `state_mean(xs::AbstractVector{<:AbstractVector}, w::UKFWeights)` computes the weighted mean of the vector of vectors of state sigma points.
  * `state_cov(xs::AbstractVector{<:AbstractVector}, m, w::UKFWeights)` where the first argument represent state sigma points and the second argument, represents the weighted mean of those points. The function should return the covariance matrix of the state sigma points weighted by `w`.

See [`UKFMeasurementModel`](@ref) for more details on how to set up a custom measurement model. Pass the custom measurement model as the second argument to the UKF constructor.

# Custom Cholesky factorization

The UnscentedKalmanFilter supports providing a custom function to compute the Cholesky factorization of the covariance matrices for use in sigma-point generation.

If either of the following conditions are met, you may experience failure in internal Cholesky factorizations:

  * The dynamics noise or measurement noise covariance matrices ($R_1, R_2$) are singular
  * The measurement is augmented and the measurement noise has fewer degrees of freedom than the number of measurements
  * (Under specific technical conditions) The dynamics is augmented and the dynamics noise has fewer degrees of freedom than the number of state variables. The technical conditions are easiest to understand in the linear-systems case, where it corresponds to the Riccati equation associated with the Kalman gain not having a solution. This may happen when the pair $(A, R1)$ has uncontrollable modes on the unit circle, for example, when there are integrating modes that are not affected through the noise.

The error message may look like

```
ERROR: PosDefException: matrix is not positive definite; Factorization failed.
```

In such situations, it is advicable to reconsider the noise model and covariance matrices, alternatively, you may provide a custom Cholesky factorization function to the UKF constructor through the keyword argument `cholesky!`. The function should have the signature `cholesky!(A::AbstractMatrix)::Cholesky`. A useful alternative factorizaiton when covariance matrices are expected to be singular is `cholesky! = R->cholesky!(Positive, Matrix(R))` where the "positive" Cholesky factorization is provided by the package PositiveFactorizations.jl, which must be manually installed and loaded by the user.
