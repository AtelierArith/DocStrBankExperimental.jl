```
FirstOrder{EM} <: AbstractApproximationModel
```

First-order approximation model.

### Fields

  * `exp` – (optional, default: `BaseExp`) exponentiation method

### Algorithm

The transformations are [LeGuernicG10](@cite):

  * $Φ ← \exp(Aδ)$,
  * $Ω_0 ← CH(\mathcal{X}_0, Φ\mathcal{X}_0 ⊕ δU ⊕ B_ε)$

where $B_ε$ is the input ball of radius $ε$ centered in the origin.
