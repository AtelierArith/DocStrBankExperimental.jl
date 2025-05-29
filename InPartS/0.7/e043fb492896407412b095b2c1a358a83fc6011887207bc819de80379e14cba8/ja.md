```
    RealTimeCallback(interval, affect!; [offset=0.0, reset_on_freeze = false, initialize, finalize])
```

`affect`を[`prepropagate!`](@ref)フックで毎`interval`秒のシステム時間ごとに実行するコールバックを返します。**最初の実行から`offset`秒後に開始します**。`initialize`および`finalize`関数は、コールバックが最初に実行されたときと、シミュレーションが正常に終了したときにそれぞれ呼び出されます。

[`freeze!`](@ref)およびその後の[`defrost!`](@ref)におけるタイマーの動作は、`reset_on_freeze`キーワード引数によって設定されます。`false`（デフォルトオプション）に設定されている場合、コールバックは次の`affect`呼び出しまでの残り秒数を記憶し、解凍後に中断したところから再開します。`true`に設定されている場合、タイマーは完全にリセットされ、解凍後に再び`offset`秒待機します。
