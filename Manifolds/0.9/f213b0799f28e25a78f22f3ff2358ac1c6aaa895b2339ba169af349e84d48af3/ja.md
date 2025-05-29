```
rand(::GeneralizedStiefel; vector_at=nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、標準偏差`σ`の（ガウス）行列を生成することによって、[`GeneralizedStiefel`](@ref)多様体`M`上のランダム（ガウス）点`p`を返します。そして、（一般化された）直交化されたバージョン、すなわち、サイズ$n×k$のランダム行列のQR分解のQ成分の多様体への射影を返します。

`vector_at`が`nothing`でない場合、平均ゼロおよび標準偏差`σ`の（ガウス）ランダムベクトルを接空間$T_{vector\_at}\mathrm{St}(n,k)$から返します。これは、`vector_at`での接ベクトルへのランダム行列の射影によって行われます。 ```
