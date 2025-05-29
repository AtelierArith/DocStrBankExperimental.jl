```
(dvecf2c, BSf2c) = ghwt_f2c_bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart;
                                      cfspec::Any = 1.0, flatten::Any = 1.0,
                                      j_start::Int = 1, j_end::Int = size(dmatrix,2),
                                      useParent::Bool = true)
```

GHWT展開係数の行列から細かいから粗いベスト基底を選択します

### 入力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の行列
  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `cfspec::Any`: 使用するコスト関数の仕様 (デフォルト: 1.0、すなわち1ノルム)
  * `flatten::Any`: ベクトル値データをスカラー値データにフラット化する方法 (デフォルト: 1.0、すなわち1ノルム)
  * `useParent::Bool`: 親と子が同じコストを持つ場合に選択したベスト基底部分空間を親に更新するかどうかを示すフラグ (デフォルト = true)

### 出力引数

  * `dvecf2c::Matrix{Float64}`: 細かいから粗いベスト基底に対応する展開係数のベクトル
  * `BSf2c::BasisSpec`: 細かいから粗いベスト基底を指定するBasisSpecオブジェクト
