```
simulate_signal(sequence, partitioned_parameters::AbstractVector{<:SimulationParameters})
```

ボクセルの数が中間の `magnetization` 配列を保存するには大きすぎる場合、信号はバッチで計算できます：ボクセルは（ユーザーによって）パーティションに分割され、各パーティションについて信号が別々に計算されます。最終的な信号は、すべてのパーティションからの信号の合計です。
