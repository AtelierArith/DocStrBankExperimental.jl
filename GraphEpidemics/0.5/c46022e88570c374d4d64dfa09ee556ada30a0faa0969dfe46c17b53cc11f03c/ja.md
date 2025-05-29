`AbstractEpiModel`

すべての疫学モデルのための抽象スーパタイプ。`run_complex_contagion`で使用するためには、サブタイプは以下を実装する必要があります。

  * `model_states(::model)` はモデルの状態を説明するシンボルのタプルを返します
  * `spreading_states(::model)` は感染者の状態、感染される予定の状態（からとまで）およびレートを説明する遷移の辞書を返します。例: `Dict(:I=>[(:S,:I, x.beta)])`
  * `trans_independent(::model)` はレートを持つすべての独立した遷移のリストです（例: SIRモデルの場合は `[(:I,:R, x.gamma)]`）
  * `first_active_states(::model)` はシード状態を説明します（例: SIRの場合は `(:I,)`）
