```
predict(m::LinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number})
predict(m::LinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number}, rng::AbstractRNG)
```

線形動力学モデルを使用して、制御入力 u を用いて状態 x を時間的に1ステップ前進させます。rng が指定されている場合、プロセスノイズが追加されます。
