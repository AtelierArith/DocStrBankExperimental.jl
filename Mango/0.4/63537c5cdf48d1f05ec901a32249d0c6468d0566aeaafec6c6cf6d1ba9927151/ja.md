```
run_with_mqtt(runnable::Function,
n_container::Int,
agent_tuples::Tuple...;
broker_host::String="127.0.0.1",
broker_port::Int=1883,
codec::Union{Nothing,Tuple{Function,Function}}=(encode, decode))
```

エージェントをMQTTコンテナで実行します（リアルタイム）。

指定された`agents`を`n_container`（リアルタイムコンテナ）に分配し、コンテナがアクティブに実行されている間に`runnable`（コンテナリストを引数として受け取る）を実行します。エージェントごとに補足情報をTupleとして追加することが可能です。例えば、`(Agent, :aid => "my_aid", :topics => ["topic"])`のように。ここで、MQTTコンテナは`broker_host`上のブローカーと`broker_port`で作成されます。コンテナにはクライアントID（client1、client2 ...）が割り当てられます。
