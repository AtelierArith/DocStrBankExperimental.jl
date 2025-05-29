```
server_0mq4lv(fns=(;); initOK=false)
```

`server_0mq4lv`（LabView用のゼロMQを意味します）は、パッケージのトップレベル関数です。ユーザー関数はNamedTupleまたはDictとして提供する必要があります。ZMQソケットを開始し、リクエストをリッスンし、それらを解析し、要求されたユーザー関数を実行し、応答を送信します。繰り返します。

# 引数

  * `initOK`: ユーザースクリプトのチェックをスキップするには、`true`に設定します。

# 例

```julia-repl

julia> server_0mq4lv((;foo=foo, bar, baz))
```
