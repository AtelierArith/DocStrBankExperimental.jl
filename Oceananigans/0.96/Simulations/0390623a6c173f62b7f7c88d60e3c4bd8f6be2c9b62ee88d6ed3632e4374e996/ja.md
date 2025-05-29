```
run!(simulation; pickup=false)
```

`simulation`を実行し、`simulation.stop_criteria`のいずれかが`true`と評価されるまで実行します。シミュレーションはその後停止します。

# チェックポイントからのシミュレーションの再開

シミュレーションは、`pickup`が`true`、`String`、または0より大きい`Integer`のいずれかである場合にチェックポイントから「再開」されます。

シミュレーションを再開すると、フィールドおよび傾向データが指定されたチェックポイントに設定され、他のすべてのモデルプロパティは変更されません。

`pickup`の可能な値は次のとおりです：

  * `pickup=true`は、`simulation.output_writers`内の`Checkpointer`に関連付けられた最新のチェックポイントからシミュレーションを再開します。
  * `pickup=iteration::Int`は、`iteration`に関連付けられたチェックポイントファイルからシミュレーションを再開します。
  * `pickup=filepath::String`は、`filepath`内のチェックポインターデータからシミュレーションを再開します。

`pickup=true`および`pickup=iteration`は、`simulation.output_writers`に複数のチェックポインタが含まれている場合に失敗します。
