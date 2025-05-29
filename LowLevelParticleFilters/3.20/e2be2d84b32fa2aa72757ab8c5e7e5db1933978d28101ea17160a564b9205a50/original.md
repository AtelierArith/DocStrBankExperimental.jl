```
RBPF{IPD,IPM,AUGD}(N::Int, kf, dynamics, nl_measurement_model::AbstractMeasurementModel, R1n, d0n; An, nu::Int, Ts=1.0, p=NullParameters(), names, rng = Xoshiro(), resample_threshold=0.1)
```

Rao-Blackwellized particle filter, also called "Marginalized particle filter". The filter is effectively a particle filter where each particle is a Kalman filter that is responsible for the estimation of a linear sub structure.

!!! warning "Experimental"
    This filter is currently considered experimental and the user interface may change in the future without respecting semantic versioning.


The filter assumes that the dynamics follow "model 2" in the reference below, i.e., the dynamics is described by

$$
 \begin{align}
     x_{t+1}^n &= f_n(x_t^n, u, p, t) + A_n(x_t^n, u, p, t) x_t^l + w_t^n, \quad &w_t^n \sim \mathcal{N}(0, R_1^n) \\
     x_{t+1}^l &= A(...) x_t^l + Bu + w_t^l, \quad &w_t^l \sim \mathcal{N}(0, R_1^l) \\
     y_t &= g(x_t^n, u, p, t) + C(...) x_t^l + e_t, \quad &e_t \sim \mathcal{N}(0, R_2)
 \end{align}
$$

where $x^n$ is a subset of the state that has nonlinear dynamics, and $x^l$ is the linear part of the state. The entire state vector is represented by a special type [`RBParticle`](@ref) that behaves like the vector `[xn; xl]`, but stores `xn, xl` and the covariance `R` or `xl` separately.

  * `N`: Number of particles
  * `kf`: The internal Kalman filter that will be used for the linear part. This encodes the dynamics of the linear subspace. The matrices $A, B, C, D, R_1^l$ of the Kalman filter may be functions of `x, u, p, t` that return a matrix. The state `x` received by such functions is of type [`RBParticle`](@ref) with the fields `xn` and `xl`.
  * `dynamics`: The nonlinear part $f_n$ of the dynamics of the nonlinear substate `f(xn, u, p, t)`
  * `nl_measurement_model`: An instance of [`RBMeasurementModel`](@ref) that stores $g$ and the measurement noise distribution $R_2$.
  * `R1n`: The noise distribution of the nonlinear state dynamics, this may be a covariance matrix or a distribution. If `An = nothing`, this may be any distribution, otherwise it must be an instance of `MvNormal` or `SimpleMvNormal`.
  * `d0n`: The initial distribution of the nonlinear state $x_0^n$.
  * `An`: The matrix that describes the linear effect on the nonlinear state, i.e., $A_n x^l$. This may be a matrix or a function of $x, u, p, t$ that returns a matrix. Pass `An = nothing` if there is no linear effect on the nonlinear state. The `x` received by such a function is of type [`RBParticle`](@ref) with the fields `xn` and `xl`.
  * `nu`: The number of control inputs
  * `Ts`: The sampling time
  * `p`: Parameters
  * `names`: Signal names, an instance of [`SignalNames`](@ref)
  * `rng`: Random number generator
  * `resample_threshold`: The threshold for resampling

Based on the article ["Marginalized Particle Filters for Mixed Linear/Nonlinear State-space Models" by Thomas Schön, Fredrik Gustafsson, and Per-Johan Nordlund](https://people.isy.liu.se/rt/schon/Publications/SchonGN2004.pdf)

## Extended help

The paper contains an even more general model, where the linear part is linearly affected by the nonlinear state. It further details a number of special cases in which possible simplifications arise. 

  * If `C == 0` and `D == 0`, the measurement is not used by the Kalman filter and we may thus have an arbitrary probability distribution for the measurement noise.
  * If `An == 0`, the nonlinear state is not affected by the linear state and we may have an arbitrary probability distribution for the nonlinear state noise `R1n`. Otherwise `R1n` must be Gaussian.
