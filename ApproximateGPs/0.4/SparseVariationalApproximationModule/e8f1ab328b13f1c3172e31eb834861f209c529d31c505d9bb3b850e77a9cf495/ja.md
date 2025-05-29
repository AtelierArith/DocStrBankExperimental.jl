```
elbo(
    sva::SparseVariationalApproximation,
    fx::FiniteGP,
    y::AbstractVector{<:Real};
    num_data=length(y),
    quadrature=GPLikelihoods.DefaultExpectationMethod(),
)
```

プロセス `f = fx.f == svgp.fz.f` のエビデンス下限を [1] から計算します。ここで `y` は `fx` の観測値であり、擬似入力は `z = svgp.fz.x` によって与えられ、`q(u)` は誘導点 `u = f(z)` に対する変分分布です。

`quadrature` は `GPLikelihoods.expected_loglikelihood` に渡され、ELBO における期待対数尤度を計算するために使用されるメソッドを選択します。詳細については `GPLikelihoods.expected_loglikelihood` を参照してください。

注：尤度は観測ノイズ `fx.Σy` を持つガウス分布であると仮定されています。さらに、`fx.Σy` は等方的でなければなりません - すなわち `fx.Σy = σ² * I` です。

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
