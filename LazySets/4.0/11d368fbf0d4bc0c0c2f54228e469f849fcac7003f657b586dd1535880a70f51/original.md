```
intersection(cpa::Union{CartesianProduct,CartesianProductArray},
             P::AbstractPolyhedron)
```

Compute the intersection of a Cartesian product of a finite number of polyhedral sets with a polyhedron.

### Input

  * `cpa` – Cartesian product of a finite number of polyhedral sets
  * `P`   – polyhedron

### Output

A Cartesian product of a finite number of polyhedral sets. See the *Algorithm* section below for details about the structure.

### Notes

The restriction to polyhedral sets in `cpa` only applies to the blocks that are actually intersected with `P` (see the *Algorithm* section below for details). All other blocks are not considered by the intersection and remain identical.

### Algorithm

The underlying idea of the algorithm is to exploit the unconstrained dimensions of `P`. Without loss of generality, assume that `cpa` has the structure $X × Y × Z$ such that only the dimensions of $Y$ are constrained in $P$. By denoting a suitable projection of $P$ to the dimensions of $Y$ with $P|_Y$, we have the following equivalence:

$$
    (X × Y × Z) ∩ P = X × (Y ∩ P|_Y) × Z
$$

Note that $Y$ may still consist of many blocks. However, due to the structural restriction of a Cartesian product, we cannot break down this set further even if $P|_Y$ is still unconstrained in some dimensions of blocks in $Y$. This would require a restructuring of the dimensions. Consider this example:

$$
    Y := [0, 1] × [1, 2] × [2, 3]
    P|_Y := x₁ + x₃ ≤ 2
    Y ∩ P|_Y = 0 ≤ x₁ ∧ 1 ≤ x₂ ≤ 2 ∧ 2 ≤ x₃ ∧ x₁ + x₃ ≤ 2
$$

Even though the constraints of dimension $x₂$ are decoupled from the rest, due to the last constraint, the Cartesian product cannot be broken down further. In particular, the result $Y ∩ P|_Y$ is a polyhedron in this implementation.

Now we explain the implementation of the above idea. We first identify the dimensions in which `P` is constrained. Then we identify the block dimensions of $X × Y × Z$ such that $Y$ has minimal dimension. Finally, we convert $Y$ to a polyhedron and intersect it with a suitable projection of `P`.
