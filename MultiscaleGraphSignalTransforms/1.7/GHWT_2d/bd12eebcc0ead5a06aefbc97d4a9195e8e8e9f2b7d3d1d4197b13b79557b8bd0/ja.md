```
dvec, BSrows, BScols = ghwt_2d_bestbasis(matrix::Array{Float64,2},GProws::GraphPart,GPcols::GraphPart,
costfun_rows::Any = 1.0, costfun_cols::Any = 1.0, flatten_rows::Any = 1.0, flatten_cols::Any = 1.0)
```

行と列の重み付き再帰的分割と重み行列を備えた行列に対して、行と列の最適基底を選択するために最適基底アルゴリズムを使用して、GHWT展開係数の（冗長でない）行列を生成します。

### 入力引数

  * `matrix`              分析対象の行列
  * `GProws`              行に対する再帰的分割
  * `GPcols`              列に対する再帰的分割
  * `costfun_rows`        行に使用するコスト関数
  * `costfun_cols`        列に使用するコスト関数
  * `flatten_rows`        行のベクトル値データをスカラー値データにフラット化する方法
  * `flatten_cols`        列のベクトル値データをスカラー値データにフラット化する方法

### 出力引数

  * `dvec`                GHWT展開係数（冗長でない）
  * `BSrows`              行の最適基底
  * `BScols`              列の最適基底

Copyright 2019 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
