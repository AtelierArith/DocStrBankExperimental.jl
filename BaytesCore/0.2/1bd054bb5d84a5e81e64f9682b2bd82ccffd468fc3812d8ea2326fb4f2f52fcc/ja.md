```julia
struct IterationTempering{A<:BaytesCore.UpdateBool, T<:AbstractFloat} <: BaytesCore.TemperingMethod
```

温度の反復更新のための調整コンテナ。

# フィールド

  * `adaption::BaytesCore.UpdateBool`: 新しい反復の後に温度が更新されるかどうかをチェックします。
  * `initial::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: 調整のための初期温度。
  * `parameter::BaytesCore.TemperingParameter`: 温度調整のための調整パラメータ。
