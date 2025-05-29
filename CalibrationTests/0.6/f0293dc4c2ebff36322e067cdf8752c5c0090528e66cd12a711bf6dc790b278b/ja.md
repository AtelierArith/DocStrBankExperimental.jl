```
AsymptoticSKCETest(kernel::Kernel, predictions, targets)
```

バイアスのない二乗カーネルキャリブレーション誤差（SKCE）の推定量に基づくキャリブレーション仮説検定で、二次サンプル複雑性を持ちます。

# 詳細

データセット $\mathcal{D} = (P_{X_i}, Y_i)_{i=1,\ldots,n}$ を予測と対応するターゲットの集合とします。予測確率モデルがキャリブレーションされているという帰無仮説を $H_0$ と表します。

この仮説検定は、p値 $ℙ(\mathrm{SKCE}_{uq} > c \,|\, H_0)$ を近似します。ここで、$\mathrm{SKCE}_{uq}$ は SKCE のバイアスのない推定量で、次のように定義されます。

$$
\frac{2}{n(n-1)} \sum_{1 \leq i < j \leq n} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

ここで

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big).
\end{aligned}
$$

p値は漸近的に有効な近似に基づいて推定されます。

$$
ℙ(n\mathrm{SKCE}_{uq} > c \,|\, H_0) \approx ℙ(T > c \,|\, \mathcal{D}),
$$

ここで $T$ はブートストラップ統計量です。

$$
T = \frac{2}{n} \sum_{1 \leq i < j \leq n} \bigg(h_k\big((P^*_{X_i}, Y^*_i), (P^*_{X_j}, Y^*_j)\big)
- \frac{1}{n} \sum_{r = 1}^n h_k\big((P^*_{X_i}, Y^*_i), (P_{X_r}, Y_r)\big)
- \frac{1}{n} \sum_{r = 1}^n h_k\big((P_{X_r}, Y_r), (P^*_{X_j}, Y^*_j)\big)
+ \frac{1}{n^2} \sum_{r, s = 1}^n h_k\big((P_{X_r}, Y_r), (P_{X_s}, Y_s)\big)\bigg)
$$

は、データセット $\mathcal{D}$ のブートストラップサンプル $(P^*_{X_i}, Y^*_i)_{i=1,\ldots,n}$ に対して成り立ちます。これは次の近似に再定式化できます。

$$
ℙ(n\mathrm{SKCE}_{uq}/(n - 1) - \mathrm{SKCE}_b > c \,|\, H_0) \approx ℙ(T' > c \,|\, \mathcal{D}),
$$

ここで

$$
\mathrm{SKCE}_b = \frac{1}{n^2} \sum_{i, j = 1}^n h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big)
$$

および

$$
T' = \frac{2}{n(n - 1)} \sum_{1 \leq i < j \leq n} h_k\big((P^*_{X_i}, Y^*_i), (P^*_{X_j}, Y^*_j)\big)
- \frac{2}{n^2} \sum_{i, r=1}^n h_k\big((P^*_{X_i}, Y^*_i), (P_{X_r}, Y_r)\big).
$$

# 参考文献

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [Calibration tests in multi-class classification: A unifying framework](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx).
