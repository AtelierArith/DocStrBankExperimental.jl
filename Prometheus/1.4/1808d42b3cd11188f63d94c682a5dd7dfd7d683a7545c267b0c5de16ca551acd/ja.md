```
expose(http::HTTP.Stream, reg::CollectorRegistry = DEFAULT_REGISTRY; kwargs...)
```

`reg`内のすべてのメトリクスをHTTPストリーム`http`に書き出します。

呼び出し元は、HTTPメソッドやURIターゲットなどを確認する責任があります。HEADリクエストの場合、このメソッドはボディを書き出しません。
