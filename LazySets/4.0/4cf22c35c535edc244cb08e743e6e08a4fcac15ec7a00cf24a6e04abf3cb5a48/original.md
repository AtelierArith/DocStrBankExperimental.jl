# Extended help

```
constraints_list(Z::AbstractZonotope{<:AbstractFloat})
```

### Notes

The main algorithm assumes that the generator matrix is full rank. The result has $2 \binom{p}{n-1}$ (with $p$ being the number of generators and $n$ being the ambient dimension) constraints, which is optimal under this assumption. If this assumption is not given, the implementation tries to work around.

### Algorithm

We follow the algorithm presented in [AlthoffSB10](@citet). Three cases are not covered by that algorithm, so we handle them separately. The first case is zonotopes in one dimension. The second case is that there are fewer generators than dimensions, $p < n$, or the generator matrix is not full rank, in which case we fall back to the (slower) computation based on the vertex representation. The third case is that the zonotope is flat in some dimensions, in which case we project the zonotope to the non-flat dimensions and extend the result later.
