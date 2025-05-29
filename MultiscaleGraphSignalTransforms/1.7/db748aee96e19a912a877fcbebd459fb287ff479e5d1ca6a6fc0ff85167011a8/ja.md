```
(dvec_ngwp, BS_ngwp) = ngwp_bestbasis(dmatrix::Array{Float64,3}, GP_star::GraphPart;
                                      cfspec::Any = 1.0, flatten::Any = 1.0,
                                      j_start::Int = 1, j_end::Int = size(dmatrix, 2),
                                      useParent::Bool = true)
```

最適な基底をNGWP展開係数の行列から選択します。

# 入力引数

  * `dmatrix::Array{Float64,3}`: 展開係数の行列
  * `GP_star::GraphPart`: 双対グラフの入力GraphPartオブジェクト
  * `cfspec::Any`: 使用するコスト関数の仕様 (デフォルト = 1.0、すなわち1ノルム)
  * `flatten::Any`: ベクトル値データをスカラー値データにフラット化する方法 (デフォルト = 1.0、すなわち1ノルム)
  * `useParent::Bool`: 親と子が同じコストを持つ場合に選択された最適基底部分空間を親に更新するかどうかを示すフラグ (デフォルト = false)

# 出力引数

  * `dvec_ngwp::Matrix{Float64}`: NGWP最適基底に対応する展開係数のベクトル
  * `BS_ngwp::BasisSpec`: NGWP最適基底を指定するBasisSpecオブジェクト
