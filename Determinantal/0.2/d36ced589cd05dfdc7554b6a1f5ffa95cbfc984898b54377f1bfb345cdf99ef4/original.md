```
esp(L::AbstractLEnsemble,approx=false)
```

Compute the elementary symmetric polynomials of the L-ensemble L, e₁(L) ... eₙ(L). e₁(L) is the trace and eₙ(L) is the determinant. The ESPs determine the distribution of the sample size of a DPP:

$p(|X| = k) = \frac{e_k}{\sum_{i=1}^n e_i}$

The default algorithm uses the Newton equations, but may be unstable numerically for n large. If approx=true, a stable saddle-point approximation (as in Barthelmé et al. (2019)) is used instead for all eₖ with k>5.
