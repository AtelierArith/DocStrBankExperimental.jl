# Extended help

```
reflect(P::LazySet)
```

### Output

The set `-P`, which is either of type `HPolytope` if `P` is a polytope (i.e., bounded) or of type `HPolyhedron` otherwise.

### Algorithm

This function requires that the list of constraints of the set `P` is available, i.e., that it can be written as $P = \{z ∈ ℝⁿ: ⋂ sᵢᵀz ≤ rᵢ, i = 1, ..., N\}.$

This function can be used to implement the alternative definition of the Minkowski difference

$$
    A ⊖ B = \{a − b \mid a ∈ A, b ∈ B\} = A ⊕ (-B)
$$

by calling `minkowski_sum(A, reflect(B))`.
