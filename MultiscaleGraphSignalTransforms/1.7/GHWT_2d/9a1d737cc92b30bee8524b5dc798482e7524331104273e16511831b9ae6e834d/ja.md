```
dmatrix = ghwt_analysis_2d(matrix::Array{Float64,2}, GProws::GraphPart, GPcols::GraphPart)
```

行と列の重み付き再帰的分割と重み行列を備えた行列に対して、GHWT展開係数の冗長行列を生成します。

### 入力引数

`matrix`              分析対象の行列    `GProws`              行に対する再帰的分割    `GPcols`              列に対する再帰的分割

### 出力引数

`dmatrix`                GHWT辞書展開係数

著作権 2019 カリフォルニア大学の理事会

実装者: Yiqun Shao (指導教員: Dr. Naoki Saito)
