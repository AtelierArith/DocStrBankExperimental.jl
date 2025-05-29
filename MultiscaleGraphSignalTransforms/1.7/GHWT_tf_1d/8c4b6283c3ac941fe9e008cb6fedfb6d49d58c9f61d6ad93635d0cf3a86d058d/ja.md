(dvec, BS) = ghwt*tf*bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart; cfspec::Float64 = 1.0, flatten::Any = 1.0)

時間周波数適応GHWT法の実装 = eGHWT。Christoph M. ThieleとLars F. Villemoesによる論文「適応時間周波数タイルのための高速アルゴリズム」に基づいて修正されています。

### 入力引数

  * `dmatrix::Array{Float64,3}`: 拡張係数の行列
  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `cfspec::Any`: 使用するコスト関数の仕様 (デフォルト: 1.0、すなわち1ノルム)
  * `flatten::Any`: ベクトル値データをスカラー値データにフラット化する方法 (デフォルト: 1.0、すなわち1ノルム)

### 出力引数

  * `dvec::Matrix{Float64}`: eGHWT最適基底に対応する拡張係数のベクトル
  * `BS::BasisSpec`: eGHWT最適基底を指定するBasisSpecオブジェクト

著作権 2018 カリフォルニア大学の理事会

実装者: Yiqun Shao (アドバイザー: Dr. Naoki Saito)
