```
simulate_tribe(X_initial::Float64,
               nareas   ::Int64,
               tree_file::String;
               ωx       = 0.0,
               σ²       = 0.5,
               λ1       = 0.5,
               λ0       = 0.2,
               ω1       = 0.0,
               ω0       = 0.0,
               const_δt = 1e-4)
```

Simulate tribe model.

...

# Arguments

  * `X_initial::Float64`: trait starting value.
  * `nareas   ::Int64`: number of areas.
  * `tree_file::String`: full path to tree file.
  * `ωx::Float64 = 0.0`: simulated value of $ω_x$.
  * `σ²::Float64 = 0.5`: simulated value of $σ^2$.
  * `ω1::Float64 = 0.0`: simulated value of $ω_1$.
  * `ω0::Float64 = 0.0`: simulated value of $ω_0$.
  * `λ1::Float64 = 0.5`: simulated value of $λ_1$.
  * `λ0::Float64 = 0.2`: simulated value of $λ_0$.
  * `const_δt = 1e-4`: # delta t used to approximate the simulation (lower values

are more accurate but at a computation cost). ...
