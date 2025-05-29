```
readmetrics(m::AbstractModel; round_digits = nothing)
```

与えられたシンボリックモデルのパフォーマンスメトリックを含む`NamedTuple`を返します。パフォーマンスメトリックは、モデルの`info`構造に次のキーがある場合に計算できます：

  * `:supporting_labels`
  * `:supporting_predictions`

`round_digits`キーワード引数が提供されている場合、精度/信頼度メトリックを`round`するために使用されます。
