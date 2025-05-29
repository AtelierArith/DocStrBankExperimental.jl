```
projection_transformation!(projection::Projection,
    transfer_matrix::Matrix{<:Number}...;
    orbit::Symbol=:d)
```

Linear transformation of projection ⟨Yₗₘ|ϕₙₖ⟩.

# Arguments

  * `projection::Projection`: projection of wavefunction
  * `transfer_matrix::Matrix{<:Number}...`: transformation matrix M1, M2 ...
  * `orbit::Symbol=:d`: orbits to be considered in transformation, default d orbits
