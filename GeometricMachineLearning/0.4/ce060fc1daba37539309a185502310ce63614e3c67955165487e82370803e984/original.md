```
HRedSys
```

`HRedSys` computes the reconstructed dynamics in the full system based on the reduced one. Optionally it can be compared to the FOM solution.

It can be called using two different constructors.

# Constructors

The standard constructor is:

```julia
HRedSys(N, n; encoder, decoder, v_full, f_full, v_reduced, f_reduced, parameters, tspan, tstep, ics, projection_error)
```

where 

  * `encoder`: a function $\mathbb{R}^{2N}\mapsto{}\mathbb{R}^{2n}$
  * `decoder`: a (differentiable) function $\mathbb{R}^{2n}\mapsto\mathbb{R}^{2N}$
  * `v_full`: a (differentiable) mapping defined the same way as in GeometricIntegrators.
  * `f_full`: a (differentiable) mapping defined the same way as in GeometricIntegrators.
  * `v_reduced`: a (differentiable) mapping defined the same way as in GeometricIntegrators.
  * `f_reduced`: a (differentiable) mapping defined the same way as in GeometricIntegrators.
  * `integrator`: is used for integrating the reduced system.
  * `parameters`: a NamedTuple that parametrizes the vector fields (the same for full*vector*field and reduced*vector*field)
  * `tspan`: a tuple `(t₀, tₗ)` that specifies start and end point of the time interval over which integration is performed.
  * `tstep`: the time step
  * `ics`: the initial condition for the big system.

The other, and more convenient, constructor is:

```julia
HRedSys(odeensemble, encoder, decoder) 
```

where `odeensemble` can be a `HODEEnsemble` or a `HODEProblem`. `encoder` and `decoder` have to be neural networks. With this constructor one can also pass an integrator via the keyword argument `integrator`. The default is `ImplicitMidpoint()`.  Internally this calls the functions [`build_v_reduced`](@ref) and [`build_f_reduced`](@ref) in order to build the reduced vector fields.
