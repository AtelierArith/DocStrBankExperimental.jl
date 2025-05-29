```
NonLinModel{NT}(f::Function,  h::Function,  Ts, nu, nx, ny, nd=0; <keyword arguments>)
NonLinModel{NT}(f!::Function, h!::Function, Ts, nu, nx, ny, nd=0; <keyword arguments>)
```

Construct a nonlinear model from state-space functions `f`/`f!` and `h`/`h!`.

Both continuous and discrete-time models are supported. The default arguments assume  continuous dynamics. Use `solver=nothing` for the discrete case (see Extended Help). The functions are defined as:

$$
\begin{aligned}
    \mathbf{ẋ}(t) &= \mathbf{f}\Big( \mathbf{x}(t), \mathbf{u}(t), \mathbf{d}(t), \mathbf{p} \Big) \\
    \mathbf{y}(t) &= \mathbf{h}\Big( \mathbf{x}(t), \mathbf{d}(t), \mathbf{p} \Big)
\end{aligned}
$$

where $\mathbf{x}$, $\mathbf{y}$, $\mathbf{u}$, $\mathbf{d}$ and $\mathbf{p}$ are respectively the state, output, manipulated input, measured disturbance and parameter vectors. As a mather of fact, the parameter argument `p` can be any Julia objects but use a mutable type if you want to change them later e.g.: a vector. If the dynamics is a function of the time, simply add a measured disturbance defined as $d(t) = t$. The functions can be implemented in two possible ways:

1. **Non-mutating functions** (out-of-place): define them as `f(x, u, d, p) -> ẋ` and `h(x, d, p) -> y`. This syntax is simple and intuitive but it allocates more memory.
2. **Mutating functions** (in-place): define them as `f!(ẋ, x, u, d, p) -> nothing` and `h!(y, x, d, p) -> nothing`. This syntax reduces the allocations and potentially the  computational burden as well.

!!! tip
    Replace the `d` or `p` argument with `_` in your functions if not needed (see Examples below).


The rest of the documentation assumes discrete dynamics since all models end up in this  form. The optional parameter `NT` explicitly set the number type of vectors (default to  `Float64`).

!!! warning
    The two functions must be in pure Julia to use the model in [`NonLinMPC`](@ref), [`ExtendedKalmanFilter`](@ref), [`MovingHorizonEstimator`](@ref) and [`linearize`](@ref), except if a finite difference backend is used (e.g. [`AutoFiniteDiff`](@extref DifferentiationInterface List)).


See also [`LinModel`](@ref).

# Arguments

  * `f::Function` or `f!`: state function.
  * `h::Function` or `h!`: output function.
  * `Ts`: sampling time of in second.
  * `nu`: number of manipulated inputs.
  * `nx`: number of states.
  * `ny`: number of outputs.
  * `nd=0`: number of measured disturbances.
  * `p=[]`: parameters of the model (any type).
  * `solver=RungeKutta(4)`: a [`DiffSolver`](@ref) object for the discretization of continuous dynamics, use `nothing` for discrete-time models (default to 4th order [`RungeKutta`](@ref)).
  * `jacobian=AutoForwardDiff()`: an `AbstractADType` backend when [`linearize`](@ref) is  called, see [`DifferentiationInterface` doc](@extref DifferentiationInterface List).

# Examples

```jldoctest
julia> f!(ẋ, x, u, _ , p) = (ẋ .= p*x .+ u; nothing);

julia> h!(y, x, _ , _ ) = (y .= 0.1x; nothing);

julia> model1 = NonLinModel(f!, h!, 5.0, 1, 1, 1, p=-0.2)       # continuous dynamics
NonLinModel with a sample time Ts = 5.0 s, RungeKutta(4) solver and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> f(x, u, _ , _ ) = 0.1x + u;

julia> h(x, _ , _ ) = 2x;

julia> model2 = NonLinModel(f, h, 2.0, 1, 1, 1, solver=nothing) # discrete dynamics
NonLinModel with a sample time Ts = 2.0 s, empty solver and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    State-space functions are similar for discrete dynamics:

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &= \mathbf{f}\Big( \mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k), \mathbf{p} \Big) \\
        \mathbf{y}(k)   &= \mathbf{h}\Big( \mathbf{x}(k), \mathbf{d}(k), \mathbf{p} \Big)
    \end{aligned}
    $$

    with two possible implementations as well:

    1. **Non-mutating functions**: define them as `f(x, u, d, p) -> xnext` and  `h(x, d, p) -> y`.
    2. **Mutating functions**: define them as `f!(xnext, x, u, d, p) -> nothing` and `h!(y, x, d, p) -> nothing`.

