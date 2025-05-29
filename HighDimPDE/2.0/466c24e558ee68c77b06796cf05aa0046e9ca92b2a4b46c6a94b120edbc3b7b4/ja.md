パラメトリックファミリーのコルモゴロフ方程式を解くためのアルゴリズム。

```julia
HighDimPDE.NNKolmogorov(chain, opt)
```

引数:

  * `chain`: d次元の出力を持つチェーンニューラルネットワーク。
  * `opt`: ニューラルネットワークを訓練するためのオプティマイザー。デフォルトは `ADAM(0.1)`。

[1] Berner Julius et al. "Numerically solving parametric families of high-dimensional Kolmogorov partial differential equations via deep learning."
