```
get_odeproblem(res, prob::PEtabODEProblem; kwargs...) -> (sys, callbacks)
```

`prob`内のODEモデルをシミュレーションするための`ODEProblem`とコールバック（`CallbackSet`）を取得します。`res`はパラメータ推定結果（例：`PEtabMultistartResult`）または`prob`が期待する順序のパラメータを持つ`Vector`であることができます（[`get_x`](@ref）を参照）。

キーワード引数に関する情報は[`get_ps`](@ref)を参照してください。

他にも[`get_u0`](@ref)や[`get_odesol`](@ref)を参照してください。
