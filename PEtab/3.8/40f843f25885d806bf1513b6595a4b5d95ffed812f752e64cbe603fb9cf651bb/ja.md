```
get_odesol(res, prob::PEtabODEProblem; kwargs...)::ODESolution
```

`prob`内のODEモデルをシミュレーションして`ODESolution`を取得します。`res`はパラメータ推定結果（例：`PEtabMultistartResult`）または`prob`が期待する順序のパラメータを持つ`Vector`であることができます（[`get_x`](@ref）を参照）。

キーワード引数に関する情報は[`get_ps`](@ref)を参照してください。

他にも[`get_u0`](@ref)や[`get_odeproblem`](@ref)を参照してください。
