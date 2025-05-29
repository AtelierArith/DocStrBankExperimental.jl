```
get_ps(res, prob::PEtabODEProblem; kwargs...)
```

`prob`内のODEモデルをシミュレーションするための`ODEProblem`パラメータ値を取得します。`res`はパラメータ推定結果（例：`PEtabMultistartResult`）または`prob`が期待する順序のパラメータを持つ`Vector`であることができます（[`get_x`](@ref）を参照）。

関連情報: [`get_u0`](@ref), [`get_odeproblem`](@ref), [`get_odesol`](@ref).

## キーワード引数

  * `retmap=true`: 値を`[k1 => val1, ...]`の形式のマップとして返すかどうか。こうしたマップは`ODEProblem`を構築する際に直接使用できます。`false`の場合、`Vector`が返されます。このキーワードは`get_u0`と`get_ps`にのみ適用されます。
  * `cid::Symbol`: パラメータを返すシミュレーション条件。指定しない場合、最初のシミュレーション条件がデフォルトとなります。他の`get`関数の場合、指定された`cid`の`ODEProblem`、`u0`、または`ODESolution`が返されます。
  * `preeq_id`: 使用する潜在的な前平衡（定常状態）シミュレーションID。妥当な`preeq_id`が提供されると、ODEは最初に`preeq_id`のために定常状態にシミュレーションされます。その後、モデルは`cid`にシフトし、`cid`のパラメータが返されます。他の`get`関数の場合、指定された`cid`の`ODEProblem`、`u0`、または`ODESolution`が返されます。
