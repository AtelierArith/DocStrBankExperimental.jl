```
SaveCallback{backend}(trigger::AbstractCallback, filename, dumprng, warn, onconflict)
```

シミュレーションのスナップショットを定期的に `filename` に保存するコールバックを作成します。

# 拡張ヘルプ

`trigger` コールバックがトリガーされるたびにスナップショットが保存されます。最初のアクティベーション時に、静的なシミュレーションパラメータが保存されます。

`SaveCallback` と Simulation に対して呼び出される2引数関数 `dumprng` が `true` を返す場合、完全なRNG状態がスナップショットにダンプされます。
