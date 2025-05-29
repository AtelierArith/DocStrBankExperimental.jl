```
ComposedSchedule([(s, ps) -> T(ps...),] schedule::T, parameters)
```

`parameters.(t)` によってフィールドが与えられる `schedule`。

各ステップ `t` で、`parameters.(t)` を使って新しいパラメータのセットを取得し、最初の（オプションの）引数に基づいて新しい `schedule` を作成します。新しい `schedule(t)` が返される値です。
