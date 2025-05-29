```
box_approximation(Z::AbstractZonotope)
```

Return a tight overapproximation of a zonotope with an axis-aligned box.

### Input

  * `Z` – zonotope

### Output

A hyperrectangle.

### Algorithm

This function implements the method in [AlthoffSB10; Section 5.1.2](@citet). A zonotope $Z = ⟨c, G⟩$ can be tightly overapproximated by an axis-aligned hyperrectangle such that its center is $c$ and the radius along dimension $i$ is the column-sum of the absolute values of the $i$-th row of $G$ for $i = 1,…, p$, where $p$ is the number of generators of $Z$.
