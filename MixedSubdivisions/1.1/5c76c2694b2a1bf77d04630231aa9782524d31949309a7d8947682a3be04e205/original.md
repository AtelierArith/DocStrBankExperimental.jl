```
mixed_volume(F::Vector{<:MP.AbstractPolynomialLike}; show_progress=true, algorithm=:regeneration)
mixed_volume(𝑨::Vector{<:Matrix}; show_progress=true, algorithm=:regeneration)
```

Compute the mixed volume of the given polynomial system `F` resp. represented by the support `𝑨`. There are two possible values for `algorithm`:

  * `:total_degree`: Use the total degree homotopy algorithm described in Section 7.1
  * `:regeneration`: Use the tropical regeneration algorithm described in Section 7.2
