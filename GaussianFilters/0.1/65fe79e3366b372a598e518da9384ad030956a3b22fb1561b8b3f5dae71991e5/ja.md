```
predict(m::NonLinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number})
predict(m::NonLinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number}, rng::AbstractRNG)
```

非線形ダイナミクスモデルを使用して、制御入力uを用いて状態xを1ステップ前方に伝播させます。rngが指定されている場合、プロセスノイズが追加されます。
