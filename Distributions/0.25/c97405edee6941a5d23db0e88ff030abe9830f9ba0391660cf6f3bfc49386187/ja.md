```
Lindley(θ)
```

一変数の*リンドレー分布*は、形状パラメータ `θ > 0` を持ち、確率密度関数は次のようになります。

$$
f(x; \theta) = \frac{\theta^2}{1 + \theta} (1 + x) e^{-\theta x}, \quad x > 0
$$

この分布は最初にリンドレーによって記述され[^1]、その後ギタニーらによってより詳細に研究されました[^2]。`Lindley(θ)` は、`Exponential(θ)` と `Gamma(2, θ)` の混合であり、それぞれの混合重みは `p = θ/(1 + θ)` と `1 - p` です。

[^1]: Lindley, D. V. (1958). Fiducial Distributions and Bayes' Theorem. Journal of the   Royal Statistical Society: Series B (Methodological), 20(1), 102–107.

[^2]: Ghitany, M. E., Atieh, B., & Nadarajah, S. (2008). Lindley distribution and its   application. Mathematics and Computers in Simulation, 78(4), 493–506.
