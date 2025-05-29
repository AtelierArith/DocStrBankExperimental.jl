```
ExtremelySimpleNL(k::Int, ℓ::Int, w::Int, τ::Int, ε::Real) <: Decomposition
```

Quite literally the "extremely simple nonlinear noise-reduction method"[^Schreiber1993]. It decomposes `s` into the **sum** `x + r` with `x` being the "noiseless" timeseries. This is the average position of neighbors in the delay embedded space.

This method works well if your timeseries is composed by the addition of a structured component (which follows deterministic and stationary dynamics which the embedding should approximate) and some noise.

The cited paper has some info on choosing optimal `ε`.

Arguments:

  * `k` amount of past delay
  * `ℓ` amount of forward delay
  * `w` Theiler window
  * `τ` delay time
  * `ε` radius of the neighborhood in the embedded space

[^Schreiber1993]: [Schreiber, (1993) Extremely simple nonlinear noise-reduction method. Physical Review E, 47(4)](https://doi.org/10.1103/PhysRevE.47.2401)
