```
Scheduler(state, T)
```

`Scheduler`の便利なコンストラクタ

引数:

  * `state=EmptyState()` は `Scheduler` に使用される `AbstractState` のサブタイプ
  * `T=Float64`          `Scheduler` で時間を保持するために使用される型
  * `monitor=(s,Δ) -> nothing`  モニタ関数

デフォルトでは空の `event_queue` が作成され、`now` は `zero(T)` に設定され、アイドル状態の `monitor` があります。
