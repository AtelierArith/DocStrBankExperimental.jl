```
非同期
```

[`LShaped.AsynchronousExecution`](@ref)/[`ProgressiveHedging.AsynchronousExecution`](@ref)のファクトリオブジェクト。`Execution`属性を通過させます。

...

# パラメータ

  * `max_active::Int = 3`: 非同期で実行されるアクティブな反復の最大数。
  * `κ::T = 0.5`: 新しい反復を開始するために必要な完了したサブプロブレムの相対量。非同期性の量を制御します。

...
