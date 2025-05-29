```julia
combinatoric_factor(n) -> Any

```

Computes the combinatorial factor for graph symmetry calculations.

This function calculates the product of two factors:

1. The vertex permutation factor: number of ways to permute identical internal vertices
2. The edge endpoint permutation factor: number of ways to permute edge endpoints attached to vertices of the same degree

This factor is used in the calculation of symmetry factors for Feynman diagrams.

## Parameters

  * `n`: Vector where `n[k]` is the number of vertices with degree `k`

## Returns

  * A floating point number representing the total combinatorial factor
