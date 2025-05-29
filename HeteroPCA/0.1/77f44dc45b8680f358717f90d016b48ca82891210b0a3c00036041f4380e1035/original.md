```
HeteroPCAModel
```

Variant of PCA that jointly estimates the low‑rank common component **and** heteroscedastic idiosyncratic noise variance.  Missing cells are allowed; they are mean‑centered and then imputed with zero internally (i.e. the "zero‑fill after demeaning" strategy proposed by Cai et al., 2019).

`proj` gives an **orthonormal** basis of the estimated factor space, `prinvars` are the k largest singular values of the estimated low‑rank matrix, and `noisevars` stores the final diagonal (noise) estimates.
