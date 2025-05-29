```
set_state!(ds::DynamicalSystem, mapping::AbstractDict)
```

`set_state!` の便利なバージョンで、`mapping` のすべてのインデックス-値ペア `(i, val)` に対して `set_state!(ds, val, i)` を反復的に呼び出します。これは主に二つのケースで便利です：

1. 一部の状態変数のみを部分的に設定するため、
2. 名前で変数を設定するため（システムが ModelingToolkit.jl を介して作成された場合）

動的変数の順序を追跡する必要がなくなります。
