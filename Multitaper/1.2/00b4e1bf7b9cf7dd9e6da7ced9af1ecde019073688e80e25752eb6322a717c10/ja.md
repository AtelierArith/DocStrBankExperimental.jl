```
demodulate(x, f0, NW, blockLen; <keyword arguments>)
```

マルチテーパー複素デモジュレーション

...

# 引数

  * `x::Vector{T} where T<:Float64`: 時系列を含むベクトル
  * `f0::Float64`: 複素デモジュレートの中心周波数
  * `NW::Float64`: 時間帯域幅の積
  * `blockLen::Int64`: 使用するブロックの長さ
  * `wrapphase::Bool = true`: 位相をアンラップするかどうか
  * `dt::Float64 = 1.0`: 時系列のサンプリングレート（時間単位）
  * `basetime::Float64 = 0.0`: 時系列が始まる時刻

...

...

# 出力

  * `Demodulate`型の構造体

...
