```
Backward{EM, SO, SI, IT, BT} <: AbstractApproximationModel
```

Backward approximation model.

### Fields

  * `exp`     – exponentiation method
  * `setops`  – set operations method
  * `sih`     – symmetric interval hull
  * `inv`     – (optional, default: `false`) if `true`, assume that the state matrix              is invertible and use its inverse in the `Φ` functions
  * `backend` – (optional, default: `nothing`) used if the algorithm needs to apply              concrete polyhedral computations

### Algorithm

The transformations are:

  * $Φ ← \exp(Aδ)$,
  * $Ω_0 ← CH(\mathcal{X}_0, Φ\mathcal{X}_0 ⊕ δU(0) ⊕ E_ψ(U(0), δ) ⊕ E^-(\mathcal{X}_0, δ))$,
  * $V(k) ← δU(k) ⊕ E_ψ(U(k), δ)$.

Here we allow $U$ to be a sequence of time varying non-deterministic input sets.

For the definition of the sets $E_ψ$ and $E^-$ see [FrehseGDCRLRGDM11](@cite). The `Forward` method uses $E^+$.
