```
UCME(k, testpredictions, testtargets)
```

カーネル `k` と `testpredictions` および `testtargets` のセットを持つ非正規化キャリブレーション平均埋め込み (UCME) の推定器。

予測とターゲットの積空間上のカーネル `k` は、予測とターゲットのタプルに対して評価できる [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) の `Kernel` でなければなりません。

テスト予測とテストターゲットの数は同じでなければならず、少なくとも1つである必要があります。

# 詳細

この推定器はバイアスがあり、非負であることが保証されています。そのサンプルの複雑さは $O(mn)$ であり、ここで $m$ はテストロケーションの数、$n$ はサンプルの総数です。

$$
(T_i)_{i=1,\ldots,m}
$$

をテストロケーションのセット、すなわちテスト予測と対応するターゲットとし、$(P_{X_j}, Y_j)_{j=1,\ldots,n}$ を予測と対応するターゲットのデータセットとします。$\mathrm{UCME}_{k,m}^2$ のプラグイン推定器は次のように定義されます。

$$
m^{-1} \sum_{i=1}^{m} {\bigg(n^{-1} \sum_{j=1}^n k\big(T_i, (P_{X_j}, Y_j)\big)
- \mathbb{E}_{Z \sim P_{X_j}} k\big(T_i, (P_{X_j}, Z)\big)\bigg)}^2.
$$

# 参考文献

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx). *ICLR 2021* で発表予定。
