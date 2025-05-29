```
EventLoopGroup(num_threads::Union{Int,Nothing} = nothing, cpu_group::Union{Int,Nothing} = nothing)
```

イベントループのコレクション。イベントループは、I/Oなどの非同期作業を行うためのスレッドです。

引数:

  * `num_threads (Union{Int,Nothing}) (default=nothing)`: 作成するイベントループの最大数。指定しない場合、マシンの各プロセッサに対して1つが作成されます。
  * `cpu_group (Union{Int,Nothing}) (default=nothing)`: すべてのスレッドがピン留めされるオプションのプロセッサグループ。非一様メモリアクセス (NUMA) ノードを持つシステムに便利です。指定された場合、スレッドの数はグループ内のプロセッサの数に制限されます。
