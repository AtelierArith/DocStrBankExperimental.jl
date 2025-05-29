```
get_u0(res, prob::PEtabODEProblem; kwargs...)
```

`prob`内のODEモデルをシミュレーションするための`ODEProblem`初期値を取得します。`res`はパラメータ推定結果（例：`PEtabMultistartResult`）または`prob`が期待する順序のパラメータを持つ`Vector`であることができます（[`get_x`](@ref）を参照）。

キーワード引数に関する情報は[`get_ps`](@ref)を参照してください。

他に[`get_odeproblem`](@ref)および[`get_odesol`](@ref)も参照してください。
