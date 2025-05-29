```
sherrington_kirkpatrick(variance::Float64; seed::Float64=1.0, num_layers::Int=1, driver=X)
```

シャリントン-カークパトリックモデルのインスタンスを設定するラッパー関数。

### 入力

  * `N::Int`: 問題のスピンの数。
  * `variance::Float64`: 結合行列の分布の分散。
  * `seed::Float64=1.0`: 結合行列で使用される乱数生成器のシード。
  * `num_layers::Int=1` (オプション): 通常$p$で示されるQAOA層の数。
  * `driver=X` (オプション): QAOAで使用されるドライバーまたはミキサー。

### 出力

  * すべての関連量を保持する`Problem`構造体のインスタンス。

### 注意事項

シャリントン-カークパトリックモデルのコスト関数は

$$
\hat H_P = \frac{1}{\sqrt{N}}\sum_{i<j\leq N} J_{ij} \hat{Z}_i \hat{Z}_j,
$$

であり、結合$J_{ij}$はi.i.d.標準ガウス変数、すなわち平均がゼロ$\langle J_{ij} \rangle = 0$で分散が$\langle J_{ij}^2 \rangle = J^2$です。
