```
seqd = DiscreteSequence(Gx, Gy, Gz, B1, Δf, ADC, t, Δt)
```

指定された時間でのイベント振幅のベクトルを含むSequence構造体のサンプリング版です。DiscreteSequenceはシミュレーションに使用される構造体です。

# 引数

  * `Gx`: (`::AbstractVector{T<:Real}`, `[T/m]`) x勾配ベクトル
  * `Gy`: (`::AbstractVector{T<:Real}`, `[T/m]`) y勾配ベクトル
  * `Gz`: (`::AbstractVector{T<:Real}`, `[T/m]`) z勾配ベクトル
  * `B1`: (`::AbstractVector{Complex{T<:Real}}`, `[T]`) RF振幅ベクトル
  * `Δf`: (`::AbstractVector{T<:Real}`, `[Hz]`) RFキャリア周波数変位ベクトル
  * `ADC`: (`::AbstractVector{Bool}`) ADCサンプルベクトル
  * `t`: (`::AbstractVector{T<:Real}`, `[s]`) 時間ベクトル
  * `Δt`: (`::AbstractVector{T<:Real}`, `[s]`) デルタ時間ベクトル

# 戻り値

  * `seqd`: (`::DiscreteSequence`) DiscreteSequence構造体
