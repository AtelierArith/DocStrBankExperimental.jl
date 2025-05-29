```
StickEvent(timestamp::DateTime, direc::Direc, state::State)
```

ジョイスティックイベントからのデータ。この型には以下のフィールドが含まれています：

  * `timestamp` : イベントが発生した時刻の `DateTime`。
  * `direc` : イベントの方向、`UP`、`DOWN`、`LEFT`、`RIGHT`、`MIDDLE` のいずれか（`MIDDLE` はボタンが押されたときに発生します）。
  * `state` : イベントの状態（`PRESS`、`RELEASE`、`HOLD`）。
