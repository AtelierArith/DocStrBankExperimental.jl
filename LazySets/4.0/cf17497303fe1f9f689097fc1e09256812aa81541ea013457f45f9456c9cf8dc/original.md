```
ρ(d::AbstractVector, lm::LinearMap; kwargs...)
```

Evaluate the support function of the linear map.

### Input

  * `d`      – direction
  * `lm`     – linear map
  * `kwargs` – additional arguments that are passed to the support function             algorithm

### Output

The evaluation of the support function in the given direction. If the direction has norm zero, the result depends on the wrapped set.

### Notes

If $L = M⋅S$, where $M$ is a matrix and $S$ is a set, it follows that $ρ(d, L) = ρ(M^T d, S)$ for any direction $d$.
