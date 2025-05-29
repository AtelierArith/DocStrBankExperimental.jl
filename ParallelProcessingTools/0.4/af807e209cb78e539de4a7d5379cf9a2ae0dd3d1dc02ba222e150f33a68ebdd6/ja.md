```
worker_resources
```

現在利用可能な分散Juliaワーカープロセスのリソースを取得します。

すべてのプロセスでコードをロードする必要があるため、これには時間がかかる場合があります。ワーカーリソースを照会する前に自動的に`ensure_procinit()`が実行されます。

注意: CPU ID情報は、[`ThreadPinning`](https://github.com/carstenbauer/ThreadPinning.jl)がロードされている場合にのみ利用可能です。
