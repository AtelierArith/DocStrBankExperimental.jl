```
normscale(flat::ModulatedFourierLattice, expon::Real, 
          Gs::Union{ReciprocalBasis, Nothing} = nothing)  --> ModulatedFourierLattice
```

展開係数の逆軌道ノルム再スケーリングをノルム指数 `expon` で適用します。`Gs` が何も指定されていない場合、軌道ノルムは格子基底で計算されるため（したがって、厳密にはノルムではありません）、`Gs` を [`ReciprocalBasis`](@ref) として提供することで、ノルムが直交座標系で正しく評価されます。さらに詳しい議論は [`modulate`](@ref) を参照してください。

インプレースの同等の関数は [`normscale!`](@ref) で提供されています。
