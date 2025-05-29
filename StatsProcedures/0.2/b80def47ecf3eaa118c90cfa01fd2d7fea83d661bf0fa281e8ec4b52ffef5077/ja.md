```
PooledStatsProcedure
```

手順と共有ステップのコレクション。

`PooledStatsProcedure`のインスタンスは、同一のステップを繰り返すのを避けるのに役立つ方法で、共有ステップの中でインデックス付けされ、反復可能です。詳細は[`pool`](@ref)を参照してください。

# フィールド

  * `procs::Vector{AbstractStatsProcedure}`: [`AbstractStatsProcedure`](@ref)のコレクション。
  * `steps::Vector{SharedStatsStep}`: ソートされた[`SharedStatsStep`](@ref)。
