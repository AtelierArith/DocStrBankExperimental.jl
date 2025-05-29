```
SpecifiedTimes(times)
```

指定された `times` の値がモデルの時計と等しいときに「実行」する（出力またはコールバックの実行をスケジュールする）呼び出し可能な `TimeInterval` を返します。例えば、

  * `SpecifiedTimes([1, 15.3])` は `model.clock.time` が `1` および `15.3` のときに実行されます。

!!! info "指定された時間のソート"
    指定された `times` は順序付けられている必要はなく、`SpecifiedTimes` コンストラクタは必要に応じてそれらを昇順にチェックして順序付けます。

