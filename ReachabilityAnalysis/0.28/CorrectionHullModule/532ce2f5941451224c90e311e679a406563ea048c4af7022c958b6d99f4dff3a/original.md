```
CorrectionHull{EM} <: AbstractApproximationModel
```

Discretization using the correction hull of the matrix exponential.

### Fields

  * `exp`   – exponentiation method
  * `order` – order of the Taylor series expansion of the matrix exponential

### Algorithm

For the homogeneous case, this method implements the transformation:

$$
Ω_0 = CH(X_0, e^{Aδ}  X_0) ⊕ FX_0
$$

where $F$ is the correction (interval) matrix.

For the inhomogeneous case, $x' = Ax + u$,  $x ∈ X, u ∈ U$, implements $Ω_0 = CH(X_0, exp(Aδ)  X0) ⊕ FX0$ where $F$ is the correction (interval) matrix.

In both cases, if $A$ is an interval matrix, the exponential is overapproximated using methods from `IntervalMatrices.jl`.
