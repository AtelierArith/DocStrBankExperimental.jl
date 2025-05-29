```
OutputCollector(cmd::AbstractCmd; verbose::Bool = false)
```

`cmd`を実行し、`stdout`と`stderr`の出力を独立してキャプチャしつつ、各行の時間を記録して、独立して保存/分析できるようにしますが、同期的に再生できるようにします。
