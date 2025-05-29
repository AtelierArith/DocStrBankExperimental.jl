```
info(m::AbstractModel)::NamedTuple = m.info
info(m::AbstractModel, key) = m.info[key]
info(m::AbstractModel, key, defaultval)
```

モデル `m` の `info` 構造体を返します。この構造体は、モデルの動作に影響を与えない追加情報を格納するために使用されます。

この構造体は、例えば、学習フェーズ中のモデルの統計的パフォーマンスに関する情報を保持できます。

さらに [`AbstractModel`](@ref)、[`info!`](@ref) を参照してください。
