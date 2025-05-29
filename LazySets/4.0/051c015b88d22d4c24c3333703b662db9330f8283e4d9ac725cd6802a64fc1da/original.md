```
σ(d::AbstractVector, eprojmap::ExponentialProjectionMap;
  [backend]=get_exponential_backend())
```

Return a support vector of a projection of an exponential map.

### Input

  * `d`        – direction
  * `eprojmap` – projection of an exponential map
  * `backend`  – (optional; default: `get_exponential_backend()`) exponentiation               backend

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the wrapped set.

### Notes

If $S = (L⋅M⋅R)⋅X$, where $L$ and $R$ are matrices, $M$ is a matrix exponential, and $X$ is a set, it follows that $σ(d, S) = L⋅M⋅R⋅σ(R^T⋅M^T⋅L^T⋅d, X)$ for any direction $d$.
