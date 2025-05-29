```
overapproximate(QM::QuadraticMap{N, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

Overapproximate a quadratic map of a zonotopic set with a zonotope.

### Input

  * `QM`       – quadratic map of a zonotopic set
  * `Zonotope` – target set type

### Output

A zonotope overapproximating the quadratic map of a zonotopic set.

### Notes

Mathematically, a quadratic map of a zonotope with matrices $Q$ is defined as:

$$
    Z_Q = \right\{ λ \mid λ_i = x^T Q\^{(i)} x,~i = 1, …, n,~x ∈ Z \left\}
$$

### Algorithm

This method implements [AlthoffK12; Lemma 1](@citet).
