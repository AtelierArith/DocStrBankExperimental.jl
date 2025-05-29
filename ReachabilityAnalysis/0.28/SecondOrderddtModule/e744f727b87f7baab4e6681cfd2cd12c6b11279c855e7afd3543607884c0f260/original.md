```
SecondOrderddt{EM, SO, SI, IT, BT} <: AbstractApproximationModel
```

Second-order approximation model used in the tool `d/dt`. It can be used for overapproximation and underapproximation.

### Fields

  * `oa`      – (optional, default: `true`) flag to choose between              overapproximation and underapproximation
  * `exp`     – (optional, default: `BaseExp`) exponentiation method
  * `setops`  – (optional, default: `:lazy`) set operations method
  * `sih`     – (optional, default: `:concrete`) way to compute the symmetric              interval hull
  * `inv`     – (optional, default: `false`) if `true`, assume that the state              matrix is invertible and use its inverse in the `Φ` functions
  * `backend` – (optional, default: `nothing`) used if the algorithm needs to              apply concrete polyhedral computations

### Algorithm

The transformations are:

  * $Φ ← \exp(Aδ)$,
  * $Ω_0 ← bloat(CH(\mathcal{X}_0, Φ\mathcal{X}_0), ε)$

where $bloat(\mathcal{X}, ε)$ bloats the set $\mathcal{X}$ with the value $ε$. If `oa == false`, the bloating acts in an inverted way and shrinks the set.

### Reference

E. Asarin, T. Dang, O. Maler, O. Bournez: *Approximate reachability analysis of piecewise-linear dynamical systems*. HSCC 2000.
