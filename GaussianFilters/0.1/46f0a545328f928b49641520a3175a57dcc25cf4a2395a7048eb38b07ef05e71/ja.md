```
measure(m::LinearObservationModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number})
measure(m::LinearObservationModel, x::AbstractVector{T}, u::AbstractVector{T}, rng::AbstractRNG) where T<:Number
```

線形観測モデル m に従って、制御入力 u を用いて状態 x の観測を返します。rng が渡されると、観測に加法的ガウスノイズが加えられます。
