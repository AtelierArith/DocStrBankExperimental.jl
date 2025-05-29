```
DelayLtiSystem{T, S}(sys::StateSpace, Tau::AbstractVector{S}=Float64[]) where {T <: Number, S <: Real}
```

システムと時間遅延ベクトルの両方を指定することで遅延システムを作成します。注意：単純な入力または出力遅延を持つシステムを作成したい場合は、関数 `delay(τ)` を使用してください。
