```julia
with_connection(f, nc)

```

接続の周囲コンテキストを持つスコープを作成し、その中で関数の呼び出し時に接続引数をスキップできるようにします。

使用法:

```
    nc = NATS.connect()
    with_connection(nc) do
        publish("some.subject") # `connection` 引数は不要です。
    end
```
