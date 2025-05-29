```
Base.split(y::NamedArray, k::Int64; seed::Int64=1)
```

Split source nodes in `y` into `k` groups for cross-validation.

# Arguments

  * `y::AbstractMatrix`: Drug-Target rectangular adjacency matrix.
  * `k::Int64`: Number of groups to use in data splitting.
  * `seed::Int64`: Seed used for data splitting.
