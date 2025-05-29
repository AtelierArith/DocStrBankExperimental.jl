```
serve(h::App, host=0.0.0.0, port=8000; kws...)
serve(h::App, port::Int; kws...)
```

指定された `host` と `port` でアプリ `h` を提供します。キーワード引数は `HTTP.serve` に渡されます。

非同期 `Task` を開始します。サーバーが終了するまで Julia が待機する必要があるスクリプトでは `wait(serve(...))` を呼び出してください。
