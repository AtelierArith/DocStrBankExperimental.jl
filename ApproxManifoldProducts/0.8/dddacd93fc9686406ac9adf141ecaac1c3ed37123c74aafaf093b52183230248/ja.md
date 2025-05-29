```julia
manifoldLooCrossValidation(pts, bw; own, diffop)

```

1つの要素を除いた交差検証を用いて負のエントロピーを計算します。

# 背景

出典: Silverman, B.: Density Estimation for Statistics and Data Analysis, 1986, p.52

カーネルによって推定された確率密度関数 `p(x)`

$$
hatp_{-j}(x) = 1/(N-1) Σ_{i != j}^N frac{1}{sqrt{2pi}σ } exp{ -frac{(x-μ)^2}{2 σ^2} }
$$

および、1つの要素を除いた `hatp_{-j}(x)` の平均対数評価としての交差検証数:

$$
CV(p) = 1/N Σ_i^N log hat{p}_{-j}(x_i)
$$

この量 `CV` はエントロピー `H(p)` の推定値に関連しています:

$$
H(p) = -CV(p)
$$
