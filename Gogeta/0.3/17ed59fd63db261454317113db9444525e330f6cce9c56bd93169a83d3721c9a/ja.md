```
function NN_formulate_Psplit!(jump_model::JuMP.Model, NN_model::Flux.Chain, P, U_in, L_in; silent=true)
```

`Flux.Chain` モデルから P-split 定式化を使用して最適化問題を作成します。

パラメータ P は分割の数を指定します。

ダミー目的関数として 1 がモデルに追加されます。目的はユーザーが定義するために残されています。

# 引数

  * `jump_model`: 制約と変数はこの最適化モデルに保存されます。
  * `NN_model`: 定式化されるニューラルネットワークモデル。
  * `P`: 分割の数
  * `U_in`: 入力変数の上限。
  * `L_in`: 入力変数の下限。

# オプション引数

  * `strategy`: 分割戦略を制御します。利用可能なオプションは `equalsize` (デフォルト)、`equalrange`、`random`、`snake` です。
  * `bound_tightening`: ニューロンの境界がどのように生成されるか。利用可能なオプションは `fast` (デフォルト)、`standard`、`precomputed` です。
  * `parallel`: 標準の境界設定で使用され、定式化を高速化します。デフォルトは `false` です。
  * `U_bounds`, `L_bounds`: `precomputed` 境界緩和のみに使用される上限と下限。
  * `silent`: コンソール出力を制御します。デフォルトは true です。
