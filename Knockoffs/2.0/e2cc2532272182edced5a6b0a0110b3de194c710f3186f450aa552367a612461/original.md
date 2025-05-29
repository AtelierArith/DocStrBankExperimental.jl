```
solve_max_entropy(Σ::AbstractMatrix)
```

Solves the maximum entropy knockoff problem for fixed-X and model-X knockoffs given correlation matrix Σ. Users should call `solve_s` instead of this function. 

# Reference

Algorithm 2.2 from Powerful Knockoffs via Minimizing Reconstructability: https://arxiv.org/pdf/2011.14625.pdf

# Note

There is a typo in algorithm for computing ME knockoffs in "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020). In the supplemental section, equation 59, they needed to evaluate  `c_m = D^t_{-j,j}D^{-1}_{-j,-j}D_{-j,j}`. They claimed the FANOK paper  ("FANOK: KNOCKOFFS IN LINEAR TIME" by Askari et al. (2020)) implies that `c_m = ||v_m||^2` where `Lv_m = u`. However, according to section A.1.2 of the FANOK paper, it seems like the actual update should be `D^t_{-j,j}D^{-1}_{-j,-j}D_{-j,j} = ζ*||c_m||^2 / (ζ + ||c_m||^2)`  where `ζ = 2Σ_{jj} - s_j`.
