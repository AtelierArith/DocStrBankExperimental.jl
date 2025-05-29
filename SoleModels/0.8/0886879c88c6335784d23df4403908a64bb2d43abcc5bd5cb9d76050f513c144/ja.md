```
readmetrics(m::AbstractModel; round_digits = nothing)
```

与えられたシンボリックモデルのパフォーマンスメトリクスを含む`NamedTuple`を返します。パフォーマンスメトリクスは、モデルの`info`構造に次のキーがある場合に計算できます: 

  * :supporting*labels
  * :supporting*predictions

`round_digits`キーワード引数が提供されている場合、精度/信頼度メトリクスを`round`するために使用されます。
