```
ar(d::AbstractIdData, na; λ=0, estimator=\, scaleB=false, stochastic=false)
```

Estimate an AR transfer function `G = 1/A`, the AR process is defined as `A(z⁻¹)y(t) = e(t)`

The AR abbreviation is for "AutoRegressive model".

# Arguments:

  * `d`: IdData, see [`iddata`](@ref)
  * `na`: order of the model
  * `λ`: `λ > 0` can be provided for L₂ regularization
  * `estimator`: e.g. `\,tls,irls,rtls`
  * `scaleB`: Whether or not to scale the numerator using the variance of the prediction error.
  * `stochastic`: if true, returns a transfer function with uncertain parameters represented by `MonteCarloMeasurements.Particles`.

Estimation of AR models using least-squares is known to struggle with heavy measurement noise, using `estimator = tls` can improve the result in this case.

# Example

```jldoctest
julia> N = 10000
10000

julia> e = [-0.2; zeros(N-1)] # noise e
10000-element Vector{Float64}:
[...]

julia> G = tf([1, 0], [1, -0.9], 1) # AR transfer function
TransferFunction{Discrete{Int64}, ControlSystemsBase.SisoRational{Float64}}
   1.0z
----------
1.0z - 0.9

Sample Time: 1 (seconds)
Discrete-time transfer function model

julia> y = lsim(G, e, 1:N)[1][:] # Get output of AR transfer function from input noise e
10000-element Vector{Float64}:
[...]

julia> Gest = ar(iddata(y), 1) # Estimate AR transfer function from output y
TransferFunction{Discrete{Float64}, ControlSystemsBase.SisoRational{Float64}}
          1.0z
-------------------------
1.0z - 0.8999999999999998

Sample Time: 1.0 (seconds)
Discrete-time transfer function model

julia> G ≈ Gest # Test if estimation was correct
true

julia> eest = lsim(1/Gest, y, 1:N)[1][:] # recover the input noise e from output y and estimated transfer function Gest
10000-element Vector{Float64}:
[...]

julia> isapprox(eest, e, atol = eps()) # input noise correct recovered
true 
```
