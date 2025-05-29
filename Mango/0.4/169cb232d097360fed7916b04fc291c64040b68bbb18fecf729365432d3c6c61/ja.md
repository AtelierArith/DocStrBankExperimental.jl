```
run_with_tcp(runnable::Function,
n_container::Int,
agents::Agent...;
host::String="127.0.0.1",
start_port::Int=5555,
codec::Union{Nothing,Tuple{Function,Function}}=(encode, decode))
```

`agents`をtcpコンテナで実行します（リアルタイム）。

指定された`agents`を`n_container`（リアルタイムコンテナ）に分配し、コンテナがアクティブな間に`runnable`（コンテナリストを引数として受け取る）を実行します。ここでは、`host`上で`start_port`から始まるポートでTCPコンテナが作成されます。
