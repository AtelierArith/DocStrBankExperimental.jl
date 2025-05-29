```
run_with_tcp(runnable::Function,
n_container::Int,
agent_tuples::Union{Tuple,Agent}...;
host::String="127.0.0.1",
start_port::Int=5555,
codec::Union{Nothing,Tuple{Function,Function}}=(encode, decode))
```

エージェントをtcpコンテナで実行します（リアルタイム）。

指定された`agent_tuples`を`n_container`（リアルタイムコンテナ）に分配し、コンテナがアクティブに実行されている間に`runnable`（コンテナリストを引数として受け取る）を実行します。エージェントごとに補足情報をTupleとして追加することが可能です。例えば、`(Agent, :aid => "my_aid")`のように。ここで、TCPコンテナは`host`上で`start_port`から始まるポートで作成されます。
