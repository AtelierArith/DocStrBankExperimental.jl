```
σ(d::AbstractVector, em::ExponentialMap;
  [backend]=get_exponential_backend())
```

Return a support vector of an exponential map.

### Input

  * `d`       – direction
  * `em`      – exponential map
  * `backend` – (optional; default: `get_exponential_backend()`) exponentiation              backend

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the wrapped set.

### Notes

If $E = \exp(M)⋅X$, where $M$ is a matrix and $X$ is a set, it follows that $σ(d, E) = \exp(M)⋅σ(\exp(M)^T d, X)$ for any direction $d$.
