```
update_normalizing_constants!(Q::AbstractMatrix{T}, q::AbstractVector{T})
```

Computes normalizing constants recursively using equation (5).

# Inputs

  * `Q`: `K × K × p` array. `Q[:, :, j]` is a `K × K` matrix of transition   probabilities for `j`th state, i.e. Q[l, k, j] = P(X*{j} = k | X*{j - 1} = l).   The first transition matrix is not used.
  * `q`: `K × 1` vector of initial probabilities

# todo: efficiency
