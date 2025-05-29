```
neural([rng,] network; transform=log, inverse=exp)
```

Initialize the Lux.jl neural network, `network`, and return a callable object, `model`, for solving the associated one-dimensional neural ODE for volume growth, as detailed under "Underlying ODE" below.

The returned object, `model`, is called like this:

```
volumes = model(times, p)
```

where `p` should have properties `v0`, `v∞`, `θ`, where `v0` is the initial volume (so that `volumes[1] = v0`), `v∞` is a volume scale parameter, and `θ` is a `network`-compatible Lux.jl parameter.

It seems that calibration works best if `v∞` is frozen.

The form of `θ` is the same as `TumorGrowth.initial_parameters(model)`, which is also the default initial value used when solving an associated [`CalibrationProblem`](@ref).

```julia
using Lux, Random

# define neural network with 1 input and 1 output:
network = Lux.Chain(Dense(1, 3, Lux.tanh; init_weight=Lux.zeros64), Dense(3, 1))

rng = Xoshiro(123)
model = neural(rng, network)
θ = TumorGrowth.initial_parameters(model)
times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
v0, v∞ = 0.00023, 0.00015
p = (; v0, v∞, θ)

julia> volumes = model(times, p) # (constant because of zero-initialization)
6-element Vector{Float64}:
 0.00023
 0.00023
 0.00023
 0.00023# # Neural2
```

# Underlying ODE

View the neural network (with fixed parameter `θ`) as a mathematical function $f$ and write $ϕ$ for the `transform` function. Then $v(t) = v_∞ ϕ^{-1}(y(t))$, where $y(t)$ evolves according to

$dy/dt = f(y)$

subject to the initial condition $y(t₀) = ϕ(v_0/v_∞)$, where $t₀$ is the initial time, `times[1]`. We are writing $v₀$=`v0` and $v_∞$=`v∞`.

For a list of all models see [`TumorGrowth`](@ref).  See also [`CalibrationProblem`](@ref).
