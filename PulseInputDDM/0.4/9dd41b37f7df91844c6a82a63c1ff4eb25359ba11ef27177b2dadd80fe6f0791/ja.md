```
process_spike_data(μ_rnt, data)
```

引数:

  * `μ_rnt`: 1つのセッション内のすべての細胞とすべての試行のガウスフィルタ処理された単一試行発火率の `array`。`μ_rnt` は `load_neural_data` の出力です。
  * `data`: 1つのセッションのすべての試行データの `array`。`data` は `load_neural_data` の出力です。

オプション引数: 

  * `nconds`: PSTHを計算するために作成するグループの数

戻り値: 

  * `μ_ct`: 各グループの平均PSTH。
  * `σ_ct`: 各グループの1標準偏差PSTH。
