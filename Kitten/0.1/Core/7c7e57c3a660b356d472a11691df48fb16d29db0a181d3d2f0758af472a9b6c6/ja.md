```
serve(; middleware::Vector=[], handler=stream_handler, host="127.0.0.1", port=8080, async=false, parallel=false, serialize=true, catch_errors=true, docs=true, metrics=true, show_errors=true, show_banner=true, docs_path="/docs", schema_path="/schema", kwargs...)
```

独自のカスタムリクエストハンドラーでウェブサーバーを起動します。
