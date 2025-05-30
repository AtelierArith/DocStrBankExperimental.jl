```
TRARCSolver(nlp::AbstractNLPModel [, x0 = nlp.meta.x0]; kwargs...)
TRARCSolver(stp::NLPStopping; kwargs...)
```

`TRARC` 呼び出し中に使用されるすべての構造を再編成する構造体です。`TRARCSolver` 構造体を返します。

# 引数

キーワード引数には以下が含まれる場合があります：

  * `stp::NLPStopping`: このアルゴリズムのワークフローのための `Stopping` 構造体；
  * `meta::ParamData`: [`ParamData`](@ref) を参照；
  * `workspace::TRARCWorkspace`: ソルバー自体のために割り当てられた空間；
  * `TR::ARTrustRegion`: トラスト領域のパラメータ。
