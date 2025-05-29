```
NoBloating{EM, SO, IT} <: AbstractApproximationModel
```

No bloating, or discrete-time, approximation model.

### Fields

  * `exp`     – exponentiation method
  * `setops`  – set operations method
  * `inv`     – (optional, default: `false`) if `true`, assume that the state matrix              is invertible and use its inverse in the `Φ` functions

### Algorithm

The transformations are:

  * $Φ ← \exp(Aδ)$
  * $Ω_0 ← \mathcal{X}_0$
  * $V(k) ← Φ₁(A, δ)U(k)$, $k ≥ 0$.

The function $Φ₁(A, δ)$ is defined in [`Φ₁`](@ref). We allow $U$ to be a sequence of time varying non-deterministic input sets.

See also [BogomolovFFVPS18; Eq. (14)](@citet).
