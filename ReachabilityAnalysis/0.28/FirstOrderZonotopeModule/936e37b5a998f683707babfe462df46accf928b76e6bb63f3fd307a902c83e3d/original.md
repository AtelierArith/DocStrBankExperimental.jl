```
FirstOrderZonotope{EM} <: AbstractApproximationModel
```

First order approximation model that works with zonotopes.

### Fields

  * `exp` – (optional, default: `BaseExp`) exponentiation method

### Algorithm

The transformations are:

  * $Φ ← \exp(Aδ)$,
  * $Ω_0 ← bloat(zono(CH(\mathcal{X}_0, Φ\mathcal{X}_0)), α + β)$

where $bloat(\mathcal{X}, ε)$ bloats the set $\mathcal{X}$ with the value $ε$, $zono(·)$ overapproximates its argument with a zonotope, and $α$ and $β$ are factors computed for the homogeneous system and the inputs, respectively.

### Reference

A. Girard: Reachability of uncertain linear systems using zonotopes. HSCC 2005.
