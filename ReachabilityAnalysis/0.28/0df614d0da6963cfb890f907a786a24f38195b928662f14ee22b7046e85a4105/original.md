```
DiscreteTransition{RT, GT, IT⁻, IT⁺, WT} <: AbstractTransition
```

Type that encodes a discrete transition with an affine assignment of the form:

$$
    post_d(X) = (R(X ∩ G ∩ I⁻) ⊕ W) ∩ I⁺
$$

where $I⁻$ and $I⁺$  are invariants at the source and the target locations respectively, $G ⊆ \mathbb{R}^n$ is the guard set of the transition, the assignment is of the form $x^+ := Rx + w$, $w ∈ W$, $x^+ ∈ \mathbb{R}^m$ are the values after the transition, $R ∈ \mathbb{R}^{m\times n}$ is the assignment map (or reset map) and $W ⊆ \mathbb{R}^m$ is a closed and bounded convex set of non-deterministic inputs.

### Fields

  * `R`  – assignment map
  * `W`  – non-deterministic inputs
  * `G`  – guard set of the transition from the source location to the target location
  * `I⁻` – invariant at the source location
  * `I⁺` – invariant at the target location
