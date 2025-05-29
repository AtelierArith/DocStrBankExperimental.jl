```
matrix = ghwt_tf_synthesis_2d(dmatrix::Matrix{Float64}, GProws::GraphPart, GPcols::GraphPart)
```

選択された基底ベクトルの係数から行列を合成します。

### 入力引数

  * `dmatrix`: 選択された基底ベクトルのみが非ゼロで、係数が拡張されています。
  * `GProws`: 行に対する親和行列に対応します。
  * `GPcols`: 列に対する親和行列に対応します。

### 出力引数

  * `matrix`: 合成された行列

著作権 2018 カリフォルニア大学の理事会

実装者: Yiqun Shao (指導教員: Dr. Naoki Saito)
