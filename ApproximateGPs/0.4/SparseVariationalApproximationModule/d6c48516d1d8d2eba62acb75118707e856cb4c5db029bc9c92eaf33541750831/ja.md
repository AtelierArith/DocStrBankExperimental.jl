```
posterior(sva::SparseVariationalApproximation{Centered})
```

プロセス `f = sva.fz.f` に対する近似事後分布 [1] を計算します。誘導入力 `z = sva.fz.x` と誘導点に対する変分分布 `sva.q`（これは $q(u)$ を表し、`u = f(z)` です）を考慮します。テスト点 $x^*$ での近似事後分布 $f^* = f(x^*)$ は次のように与えられます：

$$
q(f^*) = \int p(f | u) q(u) du
$$

これは閉じた形で求めることができます。

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
