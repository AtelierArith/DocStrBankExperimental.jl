```
rand(::Stiefel; vector_at=nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、標準偏差`σ`を持つ（ガウス）行列を生成して、[`Stiefel`](@ref)多様体`M`上のランダム（ガウス）点`x`を返します。そして、直交化されたバージョン、すなわちサイズ$n×k$のランダム行列のQR分解のQ成分を返します。

`vector_at`が`nothing`でない場合、平均がゼロで標準偏差`σ`を持つ接空間$T_{vector\_at}\mathrm{St}(n,k)$からの（ガウス）ランダムベクトルを返します。これは、`vector_at`での接ベクトルに対してランダム行列を射影することによって行われます。 ```
