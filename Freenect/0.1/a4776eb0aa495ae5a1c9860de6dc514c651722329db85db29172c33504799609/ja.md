```julia
sync_get_tilt_state(index::Integer) -> Freenect.RawTiltState

```

ティルト状態関数は、実行ループが実行されていない場合に開始します。

返される `RawTiltState` 構造体は、安全に保存できます。
