```
set_component!(M::AbstractPowerManifold, q, p, idx...)
```

点 `q` のコンポーネントを [`AbstractPowerManifold`](@ref) `M` のインデックス `idx` で `p` に設定します。`p` は、パワーマンホールドが構築されている [`AbstractManifold`](@ref) 上の点です。
