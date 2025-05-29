```
FitState
```

[`fit!`](@ref) の呼び出し中の実行状態を格納する型です。

`FitState` オブジェクトは [`Trainer`](@ref) オブジェクトの一部です。

# フィールド

  * `epoch`: 現在のエポック番号。
  * `run_dir`: ログとチェックポイントが保存されるディレクトリ。
  * `stage`: 現在の実行ステージ。 `:training`, `:train_epoch_end`, `:validation`, `:val_epoch_end` のいずれか。
  * `step`: 現在のステップ番号。
  * `batchsize`: 現在のバッチ内のサンプル数。
  * `should_stop`: トレーニングループを停止するには `true` に設定します。
