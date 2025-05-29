```
posterior(sva::SparseVariationalApproximation{NonCentered})
```

プロセス `f = sva.fz.f` に対する近似事後分布 [1] を、誘導入力 `z = sva.fz.x` と誘導点に対する変分分布 `sva.q` を用いて計算します（これは $q(ε)$ を表し、`ε = cholesky(cov(fz)).L \ (f(z) - mean(f(z)))` です）。テスト点 $x^*$ での近似事後分布 $f^* = f(x^*)$ は次のように与えられます：

$$
q(f^*) = \int p(f | ε) q(ε) du
$$

これは閉じた形で求めることができます。

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
