```
    Settings(P::Problem; kwargs...)        The default Settings to given Problem
    Settings(; kwargs...)       The default Settings is set by Float64 type
    Settings{T<:AbstractFloat}(; kwargs...)
```

kwargs are from the fields of Settings{T<:AbstractFloat} for Float64 and BigFloat

```
        tol::T         #2^-26 ≈ 1.5e-8  general scalar
        tolN::T        #2^-26 ≈ 1.5e-8  for norms
        tolS::T        #2^-26 ≈ 1.5e-8  for identifying S
        tolL::T        #2^-26 ≈ 1.5e-8  for L
        tolG::T        #2^-27 ≈ 7.5e-9  for Greeks (beta and gamma)
        muShft::T      #2^-18 ≈ 3.8e-6  shift the mu to (1 +/- muShft)*mu
```
