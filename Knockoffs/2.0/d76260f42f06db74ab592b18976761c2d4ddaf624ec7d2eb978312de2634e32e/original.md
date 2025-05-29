```
form_emission_prob_matrix(a, θ, xi::AbstractVector)
```

# Inputs

  * `a`: `p × K` matrix with values estimated from fastPHASE (i.e. they called it the α parameter)
  * `θ`: `p × K` matrix with values estimated from fastPHASE
  * `xi`: Length `p` vector with sample `i`'s genotypes (entries 0, 1 or 2)
