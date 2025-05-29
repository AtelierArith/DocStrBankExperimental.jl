```
LatentSlice(beta)
```

Latent slice sampling algorithm by Li and Walker[^LW2023].

# Arguments

  * `beta::Real`: Beta parameter of the Gamma distribution of the auxiliary variables.

# Keyword Arguments

  * `max_proposals::Int`: Maximum number of proposals allowed until throwing an error (default: `10000`).
