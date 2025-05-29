```
ReplicaStrategy{N}
```

[`ProjectorMonteCarloProblem`](@ref) に渡すことができ、いくつのレプリカが使用されるか、どの情報が計算されて返されるかを制御する戦略のスーパークラスです。レプリカの数は `N` です。

## 具体的な実装

  * [`NoStats`](@ref): （おそらく1つの）レプリカを実行しますが、追加の情報は報告しません。
  * [`AllOverlaps`](@ref): すべてのレプリカベクトルのペア間のオーバーラップを報告します。

## インターフェース

`ReplicaStrategy{N}` のサブタイプは、以下の関数を実装する必要があります：

  * [`Rimu.replica_stats`](@ref) - レプリカ統計の名前の `String` または `Symbol` のタプルと値のタプルを返します。これらは [`ProjectorMonteCarloProblem`](@ref) によって返される `DataFrame` に報告されます。
