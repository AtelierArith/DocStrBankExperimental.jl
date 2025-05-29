```julia
struct EnsembleProblem{T, T2, T3, T4, T5} <: SciMLBase.AbstractEnsembleProblem
```

`EnsembleProblem`のメインコンストラクタ。

## キーワード引数

  * `prob`: 基本問題。
  * `prob_func`: 軌道ごとに基本問題を修正する関数。
  * `output_func`: 解から出力を抽出する関数。
  * `reduction`: 結果を集約する関数。
  * `u_init`: 集約の初期値。
  * `safetycopy`: 修正する前に問題を深くコピーするかどうか。
