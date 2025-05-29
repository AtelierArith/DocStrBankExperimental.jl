```
ipad(X::Matrix; [r_method], [m])
```

相互に絡み合った確率的要因のデカップリングに基づいてノックオフを生成します（IPAD）。これは、`X`が`X = FΛ' + E`として因子化できると仮定します。ここで、`F`は潜在因子の`n × r`のランダム行列、`Λ`は因子負荷、`E`は残差誤差です。この仮定が満たされると、ノックオフ手法を適用する際にパワー損失なしでFDRを制御できます。内部的には、`n × n`行列の固有値分解を計算する必要があります。これは、`p`次元の凸最適化問題を解く必要がある標準のモデル-Xノックオフよりも速いことが多いです。

# 入力

  * `X`: `n × p`の数値行列で、各行はサンプル、各列は共変量です。
  * `r_method`: 潜在因子の数`r`を推定するために使用される方法。選択肢には`:er`（デフォルト）、`:gr`、または`:ve`があります。
  * `m`: 生成する変数ごとの（同時）ノックオフの数、デフォルトは`m=1`です。

# 参考文献

  * Fan, Y., Lv, J., Sharifvaghefi, M. and Uematsu, Y., 2020. IPAD: stable interpretable forecasting with knockoffs inference. Journal of the American Statistical Association, 115(532), pp.1822-1834.
  * Bai, J., 2003. Inferential theory for factor models of large dimensions. Econometrica, 71(1), pp.135-171.
  * Ahn, S.C. and Horenstein, A.R., 2013. Eigenvalue ratio test for the number of factors. Econometrica, 81(3), pp.1203-1227.

```
