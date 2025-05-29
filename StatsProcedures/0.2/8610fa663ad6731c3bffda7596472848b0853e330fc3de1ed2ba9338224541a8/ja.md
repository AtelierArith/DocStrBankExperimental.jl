```
AbstractStatsProcedure{Alias, T<:NTuple{N,StatsStep} where N}
```

統計推定または推論の手続きを指定するすべての型のスーパークラスです。

インデックス付けと反復のためのフォールバックメソッドは、`AbstractStatsProcedure`のすべてのサブタイプに対して定義されています。

# パラメータ

  * `Alias::Symbol`: 見栄えを良くするための型のエイリアス。
  * `T<:NTuple{N,StatsStep}`: 手続きに関与するステップ。
