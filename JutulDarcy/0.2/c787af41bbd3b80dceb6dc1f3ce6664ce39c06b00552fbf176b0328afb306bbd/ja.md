```
simulate_reservoir(state0, model, dt;
    parameters = setup_parameters(model),
    restart = false,
    forces = setup_forces(model),
    kwarg...
)
simulate_reservoir(case;
    kwarg...
)
```

貯水池モデルをシミュレーションするための便利な関数です。この関数は内部で [`setup_reservoir_simulator`](@ref) を呼び出し、問題をシミュレーションして [`ReservoirSimResult`](@ref) を返します。キーワード引数は [`setup_reservoir_simulator`](@ref) に渡され、その関数で文書化されています。

この結果を最も一般的な出力に展開することもできます：

`wellsols, states = simulate_reservoir(...)`

ここで `wellsols` には井戸の結果が含まれ、`states` には貯水池の結果（圧力、飽和度など、貯水池領域の各セル内）が含まれます。

# 例

`output_path` 引数と `restart` 引数の両方を提供することで、シミュレーションを再起動/再開できます：

```
# 最後に解決されたステップから自動的に再起動し、シミュレーションがすでに解決されている場合は出力を返します。
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = true)

# ステップ5から再起動
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = 5)

# 最初から開始（デフォルト）
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = false)
```
