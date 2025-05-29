```
get_genotype_emission_probabilities(θ::AbstractMatrix, xj::Number, ka::Int, kb::Int, j::Int)
```

Computes P(xj | k={ka,kb}, θ): emission probabilities for genotypes. This is eq 10 of  "Gene hunting with hidden Markov model knockoffs" by Sesia et al.
