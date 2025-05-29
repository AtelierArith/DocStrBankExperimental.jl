```
compute_weights(Z::Matrix{Ti}, theta::Symbol) where Ti<:Integer
```

Compute the normalized counts of the number of sequences at hamming distance ≤ of a precomputed optimal threshold. See `Fast and accurate multivariate Gaussian modeling of protein families: Predicting residue contacts and  protein-interaction partners` [https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0092721] and in particular the Supplementary Information at section `2 Reweighting Scheme` for details.
