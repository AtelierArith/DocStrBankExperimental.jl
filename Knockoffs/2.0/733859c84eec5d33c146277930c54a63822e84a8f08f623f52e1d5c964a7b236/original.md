```
markov_knockoffs(Z::Vector{Int}, Q::Array{T, 3}, q::Vector{T})
```

Generates knockoff of variables distributed as a discrete Markov Chain with `K` states.

# Inputs

  * `Z`: Length `p` vector of `Int` where `Z[i]` is the `i`th state
  * `Q`: `K × K × p` array. `Q[:, :, j]` is a `K × K` matrix of transition   probabilities for `j`th state, i.e. Q[l, k, j] = P(X*{j} = k | X*{j - 1} = l)   The first transition matrix is not used.
  * `q`: `K × 1` vector of initial probabilities

# Reference

Equations 4-5 of "Gene hunting with hidden Markov model knockoffs" by  Sesia, Sabatti, and Candes
