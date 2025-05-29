```
simulate(state0, model, timesteps, parameters = setup_parameters(model))
simulate(state0, model, timesteps, info_level = 3)
simulate(state0, model, timesteps; <keyword arguments>)
```

与えられた初期 `state0` に対して `model` で `timesteps` のセットをシミュレートし、オプションで特定のパラメータを指定します。追加のキーワード引数は [`simulator_config`](@ref) と [`simulate!`](@ref) に渡されます。このインターフェースは主に便利さのためのものであり、シミュレーターのすべてのストレージは使用時に割り当てられ、戻ると破棄されます。同じモデルで複数のシミュレーションを実行したい場合は、代わりに [`Simulator`](@ref) をインスタンス化し、[`simulate!`](@ref) と組み合わせることをお勧めします。

# 引数

  * `state0::Dict`: 初期状態、通常は使用中の `model` のために [`setup_state`](@ref) を使用して作成されます。
  * `model::JutulModel`: 解決すべき離散化されたシステムを記述するモデル、例えば [`SimulationModel`](@ref) または [`MultiModel`](@ref)。
  * `timesteps::AbstractVector`: 希望する報告ステップのベクター。シミュレーターは `sum(timesteps)` に達するまで時間積分を行い、各報告ステップの終わりに出力を提供します。
  * `parameters=setup_parameters(model)`: モデルのデフォルトパラメータをオプションで上書きします。
  * `forces=nothing`: `nothing`（力なし）、`setup_forces(model)` からの単一の力のセット、または `timesteps` と同じ長さのそのような力の `Vector` のいずれか。
  * `restart=nothing`: 整数が提供されると、シミュレーションはそのステップから再起動を試みます。ここまたは `config` で `output_path` が提供される必要があります。
  * `config=simulator_config(model)`: 出力、線形ソルバー、時間ステップ、出力などの多くの詳細設定を保持する設定 `Dict`。

追加の引数は [`simulator_config`](@ref) に渡されます。

他に [`simulate!`](@ref)、[`Simulator`](@ref)、[`SimulationModel`](@ref)、[`simulator_config`](@ref) も参照してください。
