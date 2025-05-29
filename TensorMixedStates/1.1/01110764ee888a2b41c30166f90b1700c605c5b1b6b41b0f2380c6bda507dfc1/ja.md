```
Simulation(state[, time = 0])
Simulation(sim, state[, time = sim.time])
```

シミュレーションデータを表現し、時間とファイルデータを保存するための型です。これはrunTMSによって使用され、返されます。最初の形式はシミュレーションオブジェクトを作成します。2番目はシミュレーションオブジェクト内の状態を更新します。（`get_sim_file`も参照）

Statesに適用可能なほとんどの関数はSimulationsにも適用できます。

# フィールド

  * `state`       : システムの状態
  * `time`        : シミュレーション時間
  * `output`      : 何もない場合は出力をリダイレクトするio
  * `files`       : データを書き込むためのioまたは辞書を保持する辞書
  * `formats`     : 出力のフォーマット情報
