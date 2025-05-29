```
isfeasible(A::AbstractMatrix, b::AbstractVector, [witness]::Bool=false;
           [solver]=nothing)
```

Check for feasibility of linear constraints given in matrix-vector form.

### Input

  * `A`       – constraints matrix
  * `b`       – constraints vector
  * `witness` – (optional; default: `false`) flag for witness production
  * `solver`  – (optional; default: `nothing`) LP solver

### Output

If `witness` is `false`, the result is a `Bool`.

If `witness` is `true`, the result is a pair `(res, w)` where `res` is a `Bool` and `w` is a witness point/vector.

### Algorithm

This implementation solves the corresponding feasibility linear program.
