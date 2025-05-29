```
AsymptoticSKCETest(kernel::Kernel, predictions, targets)
```

Calibration hypothesis test based on the unbiased estimator of the squared kernel calibration error (SKCE) with quadratic sample complexity.

# Details

Let $\mathcal{D} = (P_{X_i}, Y_i)_{i=1,\ldots,n}$ be a data set of predictions and corresponding targets. Denote the null hypothesis "the predictive probabilistic model is calibrated" with $H_0$.

The hypothesis test approximates the p-value $ℙ(\mathrm{SKCE}_{uq} > c \,|\, H_0)$, where $\mathrm{SKCE}_{uq}$ is the unbiased estimator of the SKCE, defined as

$$
\frac{2}{n(n-1)} \sum_{1 \leq i < j \leq n} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

where

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big).
\end{aligned}
$$

The p-value is estimated based on the asymptotically valid approximation

$$
ℙ(n\mathrm{SKCE}_{uq} > c \,|\, H_0) \approx ℙ(T > c \,|\, \mathcal{D}),
$$

where $T$ is the bootstrap statistic

$$
T = \frac{2}{n} \sum_{1 \leq i < j \leq n} \bigg(h_k\big((P^*_{X_i}, Y^*_i), (P^*_{X_j}, Y^*_j)\big)
- \frac{1}{n} \sum_{r = 1}^n h_k\big((P^*_{X_i}, Y^*_i), (P_{X_r}, Y_r)\big)
- \frac{1}{n} \sum_{r = 1}^n h_k\big((P_{X_r}, Y_r), (P^*_{X_j}, Y^*_j)\big)
+ \frac{1}{n^2} \sum_{r, s = 1}^n h_k\big((P_{X_r}, Y_r), (P_{X_s}, Y_s)\big)\bigg)
$$

for bootstrap samples $(P^*_{X_i}, Y^*_i)_{i=1,\ldots,n}$ of $\mathcal{D}$. This can be reformulated to the approximation

$$
ℙ(n\mathrm{SKCE}_{uq}/(n - 1) - \mathrm{SKCE}_b > c \,|\, H_0) \approx ℙ(T' > c \,|\, \mathcal{D}),
$$

where

$$
\mathrm{SKCE}_b = \frac{1}{n^2} \sum_{i, j = 1}^n h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big)
$$

and

$$
T' = \frac{2}{n(n - 1)} \sum_{1 \leq i < j \leq n} h_k\big((P^*_{X_i}, Y^*_i), (P^*_{X_j}, Y^*_j)\big)
- \frac{2}{n^2} \sum_{i, r=1}^n h_k\big((P^*_{X_i}, Y^*_i), (P_{X_r}, Y_r)\big).
$$

# References

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [Calibration tests in multi-class classification: A unifying framework](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx).
