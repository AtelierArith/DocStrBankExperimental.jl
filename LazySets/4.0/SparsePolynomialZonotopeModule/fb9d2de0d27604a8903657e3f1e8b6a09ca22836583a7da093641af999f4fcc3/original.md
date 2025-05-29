```
ρ(d::AbstractVector, P::SparsePolynomialZonotope; [enclosure_method]=nothing)
```

Bound the support function of $P$ in the direction $d$.

### Input

  * `d`                – direction
  * `P`                – sparse polynomial zonotope
  * `enclosure_method` – (optional; default: `nothing`) method to use for                       enclosure; an `AbstractEnclosureAlgorithm` from the                       [`Rangeenclosures.jl`](https://github.com/JuliaReach/RangeEnclosures.jl)                       package

### Output

An overapproximation of the support function in the given direction.

### Algorithm

This method implements [Kochdumper21a; Proposition 3.1.16](@citet).
