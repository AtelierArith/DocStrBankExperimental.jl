```
ρ(d::AbstractVector, em::ExponentialMap;
  [backend]=get_exponential_backend())
```

Evaluate the support function of the exponential map.

### Input

  * `d`       – direction
  * `em`      – exponential map
  * `backend` – (optional; default: `get_exponential_backend()`) exponentiation              backend

### Output

The evaluation of the support function in the given direction.

### Notes

If $E = \exp(M)⋅X$, where $M$ is a matrix and $X$ is a set, it follows that $ρ(d, E) = ρ(\exp(M)^T d, X)$ for any direction $d$.
