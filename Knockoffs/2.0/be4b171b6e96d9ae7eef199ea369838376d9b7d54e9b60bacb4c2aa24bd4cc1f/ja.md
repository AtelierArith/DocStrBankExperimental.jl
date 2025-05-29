```
get_genotype_emission_probabilities(θ::AbstractMatrix, xj::Number, ka::Int, kb::Int, j::Int)
```

P(xj | k={ka,kb}, θ) を計算します：遺伝子型のための発生確率。これは、Sesia et al. の "Gene hunting with hidden Markov model knockoffs" の式10です。
