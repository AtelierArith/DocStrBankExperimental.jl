```
DebugTime()
```

時間を測定し、間隔を印刷します。`start=true`を使用すると、構築時にタイマーを開始できます。たとえば、アルゴリズム全体の実行時間を測定するために（追加）。

測定された時間は、指定された`time_accuracy`を使用して丸められ、[正規化](https://docs.julialang.org/en/v1/stdlib/Dates/#Dates.canonicalize)の後に印刷されます。

# キーワードパラメータ

  * `io`:            （`stdout`）デバッグを印刷するためのデフォルトストリーム。
  * `format`:        （`"$prefix %s"`）出力を印刷するためのフォーマットで、`%s`は正規化された時間です。
  * `mode`:          （`:cumulative`）合計時間を表示するか、`:iterative`を使用して毎回リセットするか。
  * `prefix`:        （`"Last Change:"`）デバッグ出力のプレフィックス（`format`を設定した場合は無視されます）
  * `start`:         （`false`）作成時にタイマーを開始するかどうかを示します。そうでなければ、最初の呼び出し時にのみ開始される可能性があります。
  * `time_accuracy`: （`Millisecond(1)`）正規化された時間を印刷する前に、この期間に時間を丸めます。
