```
tee(c::OutputCollector; colored::Bool = false, stream::IO = stdout)
```

バックグラウンドタスクを生成して、`collector` から標準出力に行を逐次出力します。オプションで色付きにすることもできます。
