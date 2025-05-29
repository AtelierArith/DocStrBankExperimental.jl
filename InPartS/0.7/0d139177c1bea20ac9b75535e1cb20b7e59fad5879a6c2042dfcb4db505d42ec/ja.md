```
ExponentialBackoffCallback(; kwargs...) <: AbstractCallback
```

最初の実行時とその後は毎 `interval` 秒ごとにトリガーされるコールバックを返します。ここで `interval` は各実行後に `factor` で乗算されますが、`max_interval` を超えることはありません。

`defrost!` が呼ばれた後は `start_interval` に戻ります。

## キーワード引数

  * `start_interval`: 初期間隔（秒単位）
  * `max_interval=Inf`: 最大間隔（秒単位）
  * `factor=2`: 各実行後に間隔が乗算される係数
  * `affect`: 実行する関数
  * `interrupt=Returns(nothing)`: シミュレーションが中断されたときに実行する関数
  * `finalize=Returns(nothing)`: シミュレーションが終了したときに実行する関数

`affect`、`interrupt`、および `finalize` は `InPartS.DynamicState` を引数として受け入れる必要があります。
