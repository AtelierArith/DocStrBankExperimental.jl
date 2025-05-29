```
sys, x0, res = newpem(
    d,
    nx;
    zeroD  = true,
    focus  = :prediction,
    h      = 1,
    stable = true,
    sys0   = subspaceid(d, nx; zeroD, focus, stable),
    metric = abs2,
    regularizer = (p, P) -> 0,
    output_nonlinearity = nothing,
    input_nonlinearity = nothing,
    nlp = nothing,
    optimizer = BFGS(
        linesearch = LineSearches.BackTracking(),
    ),
    autodiff = :forward,
    store_trace = true,
    show_trace  = true,
    show_every  = 50,
    iterations  = 10000,
    time_limit  = 100,
    x_tol       = 0,
    f_abstol    = 0,
    g_tol       = 1e-12,
    f_calls_limit = 0,
    g_calls_limit = 0,
    allow_f_increases = false,
)
```

A new implementation of the prediction-error method (PEM). Note that this is an experimental implementation and subject to breaking changes not respecting semver.

The prediction-error method is an iterative, gradient-based optimization problem, as such, it can be extra sensitive to signal scaling, and it's recommended to perform scaling to `d` before estimation, e.g., by pre and post-multiplying with diagonal matrices `d̃ = Dy*d*Du`, and apply the inverse scaling to the resulting system. In this case, we have

$$
D_y y = G̃ D_u u ↔ y = D_y^{-1} G̃ D_u u
$$

hence `G = Dy \ G̃ * Du` where $ G̃ $ is the plant estimated for the scaled iddata. Example:

```julia
Dy = Diagonal(1 ./ vec(std(d.y, dims=2))) # Normalize variance
Du = Diagonal(1 ./ vec(std(d.u, dims=2))) # Normalize variance
d̃ = Dy * d * Du
```

If a manually provided initial guess `sys0`, this must also be scaled appropriately.

# Arguments:

  * `d`: [`iddata`](@ref)
  * `nx`: Model order
  * `zeroD`: Force zero `D` matrix
  * `stable` if true, stability of the estimated system will be enforced by eigenvalue reflection using [`schur_stab`](@ref) with `ϵ=1/100` (default). If `stable` is a real value, the value is used instead of the default `ϵ`.
  * `sys0`: Initial guess, if non provided, [`subspaceid`](@ref) is used as initial guess.
  * `focus`: `prediction` or `:simulation`. If `:simulation`, the `K` matrix will be zero.
  * `h`: Prediction horizon for the prediction error filter. Large values of `h` makes the problem computationally expensive. As `h` approaches infinity, the problem approaches the `focus = :simulation` case.
  * `optimizer`: One of Optim's optimizers
  * `autodiff`: Whether or not to use forward-mode AD to compute gradients. `:forward` (default) for forward-mode AD, or `:finite` for finite differences.
  * `metric`: The metric used to measure residuals. Try, e.g., `abs` for better resistance to outliers.

The rest of the arguments are related to `Optim.Options`.

  * `regularizer`: A function of the parameter vector and the corresponding `PredictionStateSpace/StateSpace` system that can be used to regularize the estimate.
  * `output_nonlinearity`: A function of `(y::Vector, p)` that operates on the output signal at a single time point, `yₜ`, and modifies it in-place. See below for details. `p` is a vector of estimated parameters that can be optimized.
  * `input_nonlinearity`: A function of `(u::Matrix, p)` that operates on the *entire* input signal `u` at once and modifies it in-place. See below for details. `p` is a vector of estimated parameters that is shared with `output_nonlinearity`.
  * `nlp`: Initial guess vector for nonlinear parameters. If `output_nonlinearity` is provided, this can optionally be provided.

# Nonlinear estimation

Nonlinear systems on Hammerstein-Wiener form, i.e., systems with a static input nonlinearity and a static output nonlinearity with a linear system inbetween, can be estimated as long as the nonlinearities are known. The procedure is

1. If there is **a known input nonlinearity**, manually apply the input nonlinearity to the input signal `u` *before* estimation, i.e., use the nonlinearly transformed input in the [`iddata`](@ref) object `d`. If **the input nonlinearity has unknown parameters**, provide the input nonlinearity as a function using the keyword argument `input_nonlinearity` to `newpem`. This function is expected to operate on the entire (matrix) input signal `u` and modify it *in-place*.
2. If the output nonlinearity *is invertible*, apply the inverse to the output signal `y` *before* estimation similar to above.
3. If the output nonlinearity *is not invertible*, provide the nonlinear output transformation as a function using the keyword argument `output_nonlinearity` to `newpem`. This function is expected to operate on the (vector) output signal `y` and modify it *in-place*. Example:

```julia
function output_nonlinearity(y, p)
    y[1] = y[1] + p[1]*y[1]^2       # Note how the incoming vector is modified in-place
    y[2] = abs(y[2])
end
```

Please note, `y = f(y)` does not change `y` in-place, but creates a new vector `y` and assigns it to the variable `y`. This is not what we want here.

The second argument to `input_nonlinearity` and `output_nonlinearity` is an (optional) vector of parameters that can be optimized. To use this option, pass the keyword argument `nlp` to `newpem` with a vector of initial guesses for the nonlinear parameters. The nonlinear parameters are shared between output and input nonlinearities, i.e., these two functions will receive the same vector of parameters.

The result of this estimation is the linear system *without* the nonlinearities.

# Example

The following simulates data from a linear system and estimates a model. For an example of nonlinear identification, see the documentation.

```
using ControlSystemIdentification, ControlSystemsBase Plots
G = DemoSystems.doylesat()
T = 1000  # Number of time steps
Ts = 0.01 # Sample time
sys = c2d(G, Ts)
nx = sys.nx
nu = sys.nu
ny = sys.ny
x0 = zeros(nx) # actual initial state
sim(sys, u, x0 = x0) = lsim(sys, u; x0)[1]

σy = 1e-1 # Noise covariance

u  = randn(nu, T)
y  = sim(sys, u, x0)
yn = y .+ σy .* randn.() # Add measurement noise
d  = iddata(yn, u, Ts)

sysh, x0h, opt = ControlSystemIdentification.newpem(d, nx, show_every=10)

plot(
    bodeplot([sys, sysh]),
    predplot(sysh, d, x0h), # Include the estimated initial state in the prediction
)
```

The returned model is of type `PredictionStateSpace` and contains the field `sys` with the system model, as well as covariance matrices and estimated Kalman gain for a Kalman filter.

See also [`structured_pem`](@ref) and [`nonlinear_pem`](@ref).

# Extended help

This implementation uses a tridiagonal parametrization of the A-matrix that has been shown to be favourable from an optimization perspective.¹ The initial guess `sys0` is automatically transformed to a special tridiagonal modal form.  [1]: Mckelvey, Tomas & Helmersson, Anders. (1997). State-space parametrizations of multivariable linear systems using tridiagonal matrix forms.

The parameter vector used in the optimization takes the following form

```julia
p = [trivec(A); vec(B); vec(C); vec(D); vec(K); vec(x0)]
```

Where `ControlSystemIdentification.trivec` vectorizes the `-1,0,1` diagonals of `A`. If `focus = :simulation`, `K` is omitted, and if `zeroD = true`, `D` is omitted.
