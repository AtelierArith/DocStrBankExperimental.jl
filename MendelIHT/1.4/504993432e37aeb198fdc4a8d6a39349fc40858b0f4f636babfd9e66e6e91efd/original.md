```
pve(y, X, β; l = IdentityLink())
```

Estimates phenotype's Proportion of Variance Explained (PVE) by typed genotypes  (i.e. chip heritability or SNP heritability).

# Model

We compute `Var(ŷ) / Var(y)` where `y` is the raw phenotypes, `X` contains  all the genotypes, and `ŷ = Xβ` is the predicted (average) phenotype values from the statistical model β. Intercept is NOT included.
