```
calc_rasterstate(sim, raster::Symbol, f, f_returns::DataType = Nothing, ::Type{T} = Nothing)
```

ラスタのセルのために、calc_rasterとagentstateを組み合わせました。

各セルの状態に`f`を適用することによって、ラスタ`raster`の値を計算します。

`f_returns`は関数fが返す型でなければなりません。この型にはゼロ関数の実装が必要で、zero(returntype) + f(state)はf(state)と等しくなければなりません。ラスタ内のすべてのセルが同じ`DataType`を返す場合、`f_returns`は`Nothing`に設定でき、その場合`f_returns`は自動的に導出されます。

`T`は`Nothing`に設定できますが、これはパフォーマンスを低下させますが、ラスタが異なるタイプのエージェントを含む異常な場合には必要です（この場合、`agentstate_flexible`が`agentstate`の代わりに使用されます）。

これらの値を持つn次元配列（`raster`と同じ次元）を返します。

例：

次のように書く代わりに

```@example
    calc_raster(sim, :raster, id -> agentstate(sim, id, Cell).active, Bool, [ Cell ]) 
```

次のように書くことも可能です

```@example
    calc_rasterstate(sim, :raster, c -> c.active, Bool, Cell)
```

[`finish_init!`](@ref)の後にのみ呼び出すことができます。

他に[`add_raster!`](@ref)、[`calc_rasterstate`](@ref)、および[`rastervalues`](@ref)も参照してください。
