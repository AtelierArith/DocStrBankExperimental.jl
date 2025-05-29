```
IterationInterval(interval; offset=0)
```

呼び出し可能な `IterationInterval` を返します。これは、モデルのイテレーション（`offset` によって修正された）が `interval` の倍数であるときに「作動」します（出力またはコールバックの実行をスケジュールします）。

例えば、

  * `IterationInterval(100)` はイテレーション `[100, 200, 300, ...]` で作動します。
  * `IterationInterval(100, offset=-1)` はイテレーション `[99, 199, 299, ...]` で作動します。
