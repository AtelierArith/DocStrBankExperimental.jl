# Extended help

```
ρ(d::AbstractVector{M}, P::HPoly{N};
  solver=default_lp_solver(M, N)) where {M, N}
```

### Input

  * `solver` – (optional, default: `default_lp_solver(M, N)`) the backend used to             solve the linear program

### Output

If `P` is unbounded in the given direction, there are two cases:

  * If `P` is an `HPolytope`, we throw an error.
  * If `P` is an `HPolyedron`, the result is `Inf`.
