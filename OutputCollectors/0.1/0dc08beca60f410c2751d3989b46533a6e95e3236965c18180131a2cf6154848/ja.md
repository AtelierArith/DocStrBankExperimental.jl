```
merge(collector::OutputCollector; colored::Bool = false)
```

[`OutputCollector`](@ref) の stdout と stderr ストリームを行単位でマージし、キャプチャ時間でインターリーブされたすべての収集された行を含む単一の文字列を返します。 `colored` が true に設定されている場合、`stderr` を赤で印刷するための端末カラーコードを埋め込みます。
