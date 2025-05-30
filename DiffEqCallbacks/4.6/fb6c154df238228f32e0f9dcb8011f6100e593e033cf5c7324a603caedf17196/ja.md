```julia
PresetTimeCallback(tstops, user_affect!;
    initialize = DiffEqBase.INITIALIZE_DEFAULT,
    filter_tstops = true,
    kwargs...)
```

事前に設定された時間でコールバック `affect!` を呼び出すコールバックです。`tstops` やその他の操作を行う必要はありません。このコールバックは、自動的にトリガーを追加します。

## 引数

  * `tstops`: `affect!` がトリガーされる時間。
  * `user_affect!`: 時間点で使用する `affect!(integrator)` 関数。

## キーワード引数

  * `filter_tstops`: 統合の時間範囲の終わりを超える tstops をフィルタリングするかどうか。デフォルトは true です。false の場合、tstops は統合の間隔を拡張できます。
