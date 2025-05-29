```julia
struct JointTempering{A<:BaytesCore.UpdateBool, T<:AbstractFloat} <: BaytesCore.TemperingMethod
```

温度の共同更新のための調整コンテナ。

# フィールド

  * `adaption::BaytesCore.UpdateBool`: 新しい反復の後に温度が更新されるかどうかをチェックします
  * `val::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: 現在の温度。
  * `ESSTarget::BaytesCore.ValueHolder{T} where T<:AbstractFloat`: 目標効果的サンプルサイズ。
  * `weights::Vector{T} where T<:AbstractFloat`: 温度を適応させるために使用される重みのバッファ
