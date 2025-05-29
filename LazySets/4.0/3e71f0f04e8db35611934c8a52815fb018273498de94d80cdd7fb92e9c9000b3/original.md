```
matrix(rm::ResetMap)
```

Return the $A$ matrix of the affine map $A x + b, x ∈ X$ represented by a reset map.

### Input

  * `rm` – reset map

### Output

The (`Diagonal`) matrix for the affine map $A x + b, x ∈ X$ represented by the reset map.

### Algorithm

We construct the identity matrix and set all entries in the reset dimensions to zero.
