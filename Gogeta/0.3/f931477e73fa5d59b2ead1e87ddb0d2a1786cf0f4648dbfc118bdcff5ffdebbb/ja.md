```
function NN_formulate!(jump_model::JuMP.Model, NN_model::Flux.Chain, U_in, L_in; U_bounds=nothing, L_bounds=nothing, U_out=nothing, L_out=nothing, bound_tightening="fast", compress=false, parallel=false, silent=true)
```

`Flux.Chain`モデルから混合整数最適化問題を作成します。

パラメータは、どのような境界の強化と圧縮が使用されるかを指定するために使用されます。

ダミー目的関数1がモデルに追加されます。目的はユーザーが定義することになっています。

# 引数

  * `jump_model`: 制約と変数はこの最適化モデルに保存されます。
  * `NN_model`: 定式化されるニューラルネットワークモデル。
  * `U_in`: 入力変数の上限。
  * `L_in`: 入力変数の下限。

# オプション引数

  * `bound_tightening`: モード選択: "fast", "standard", "output" または "precomputed"
  * `compress`: モデルを同時に圧縮するべきか？
  * `parallel`: 境界の強化を並行して実行します。`set_solver!`関数はグローバルスコープで定義されている必要があります。ドキュメントや例を参照してください。
  * `U_bounds`: 上限。`bound_tightening="precomputed"`の場合に必要です。
  * `L_bounds`: 下限。`bound_tightening="precomputed"`の場合に必要です。
  * `U_out`: 出力変数の上限。`bound_tightening="output"`の場合に必要です。
  * `L_out`: 出力変数の下限。`bound_tightening="output"`の場合に必要です。
  * `silent`: コンソール出力を制御します。
