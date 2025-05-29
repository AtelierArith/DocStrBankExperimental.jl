```
vector(rm::ResetMap)
```

Return the $b$ vector of the affine map $A x + b, x ∈ X$ represented by a reset map.

### Input

  * `rm` – reset map

### Output

The (sparse) vector for the affine map $A x + b, x ∈ X$ represented by the reset map. The vector contains the reset value for all reset dimensions and is zero for all other dimensions.
