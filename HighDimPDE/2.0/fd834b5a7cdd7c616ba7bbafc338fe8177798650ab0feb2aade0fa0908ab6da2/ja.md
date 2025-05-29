コルモゴロフ方程式を解くためのアルゴリズム。

```julia
HighDimPDE.NNKolmogorov(chain, opt)
```

引数:

  * `chain`: d次元出力を持つチェーンニューラルネットワーク。
  * `opt`: ニューラルネットワークを訓練するためのオプティマイザ。デフォルトは `ADAM(0.1)`。

[1]Beck, Christian, et al. "Solving stochastic differential equations and Kolmogorov equations by means of deep learning." arXiv preprint arXiv:1806.00421 (2018).
