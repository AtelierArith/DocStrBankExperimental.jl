```
getcpuid(; threadid = nothing)
```

現在実行中のJuliaスレッドが動作しているCPUスレッドのIDを返します。

`threadid=nothing`（デフォルト）の場合、呼び出しスレッドから直接IDを取得します。
