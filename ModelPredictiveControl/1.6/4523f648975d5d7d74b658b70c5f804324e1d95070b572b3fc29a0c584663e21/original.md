```
Luenberger(
    model::LinModel; 
    i_ym = 1:model.ny, 
    nint_u  = 0,
    nint_ym = default_nint(model, i_ym),
    poles = 1e-3*(1:(model.nx + sum(nint_u) + sum(nint_ym))) .+ 0.5,
    direct = true
)
```

Construct a Luenberger observer with the [`LinModel`](@ref) `model`.

`i_ym` provides the `model` output indices that are measured $\mathbf{y^m}$, the rest are unmeasured $\mathbf{y^u}$. `model` matrices are augmented with the stochastic model, which is specified by the numbers of integrator `nint_u` and `nint_ym` (see [`SteadyKalmanFilter`](@ref) Extended Help). The argument `poles` is a vector of `model.nx + sum(nint_u) + sum(nint_ym)` elements specifying the observer poles/eigenvalues (near $z=0.5$ by default). The observer is constructed with a direct transmission from $\mathbf{y^m}$ if `direct=true` (a.k.a.  current observers, in opposition to the delayed/prediction form). The method computes the observer gain `K̂` with [`place`](@extref ControlSystemsBase.place) function. This estimator is allocation-free.

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = Luenberger(model, nint_ym=[1, 1], poles=[0.61, 0.62, 0.63, 0.64])
Luenberger estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 4 estimated states x̂
 2 measured outputs ym (2 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```
