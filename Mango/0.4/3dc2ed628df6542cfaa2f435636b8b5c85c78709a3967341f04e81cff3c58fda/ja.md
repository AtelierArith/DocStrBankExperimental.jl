```
run_in_real_time(runnable::Function,
n_container::Int,
container_list_creator::Function,
agent_tuple::Tuple...)
```

エージェントをコンテナ内で実行させます（リアルタイム）。

`agent_tuple` に含まれる指定されたエージェントを `n_container`（リアルタイムコンテナ）に分配し、コンテナがアクティブに実行されている間に `runnable`（コンテナリストを引数として受け取る）を実行します。エージェントごとに補足情報をタプルとして追加することが可能です。例えば `(Agent, :aid => "my_aid")` のように。コンテナの型は `container_list_creator` によって決定されます（n*container を引数として受け取り、n*container エントリを持つコンテナのリストを返す必要があります）。
