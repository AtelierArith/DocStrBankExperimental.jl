```
QKModel{T<:Real, T2<:Real}
```

Main structure containing all parameters and moments needed for the quadratic Kalman filter.

This composite model encapsulates every component necessary to specify a quadratic state-space model. It bundles together the standard state evolution parameters, measurement parameters with quadratic terms, augmented state parameters for richer dynamics, and the unconditional moments that summarize the state behavior over time. This design enables integrated filtering and smoothing procedures within a unified framework.

# Fields

  * `state::StateParams{T}`: Parameters governing the state process, defined by the equation X*t = μ + Φ X*{t-1} + Ω ε*t, where μ is the initial state mean, Φ is the state transition matrix, and Ω scales the process noise ε*t.
  * `meas::MeasParams{T}`: Parameters for the measurement model, given by Y*t = A + B X*t + α Y*{t-1} + ∑*{i=1}^M (X*t' C*i X*t) + D ε*t, including the intercept A, linear loading B, autoregressive term α, quadratic terms involving matrices C_i, and the measurement noise scaling D.
  * `aug_state::AugStateParams{T,T2}`: Parameters for the augmented state space which extend the state representation. This component includes transformed state means, transitions, and additional matrices that capture nonlinear or auxiliary features of the state process. The use of a secondary numeric type T2 facilitates compatibility with automatic differentiation.
  * `moments::Moments{T}`: The unconditional (or stationary) moments of both the state and the augmented state. This includes the long-run mean and covariance for the state dynamics as well as the augmented state, which are critical for initialization and diagnostic evaluation of the model.

# Type Parameters

  * `T`: The primary numeric type used for most parameters (e.g., Float64). It must be a subtype of Real, ensuring both numerical precision and compatibility with standard arithmetic operations.
  * `T2`: A potentially different numeric type used specifically for parameters like Lambda in AugStateParams, often employed to leverage automatic differentiation (AD) techniques.
