```
adc = ADC(N, T)
adc = ADC(N, T, delay)
adc = ADC(N, T, delay, Δf, ϕ)
```

ADC構造体は、シーケンスイベントのアナログ-デジタルコンバータ（ADC）を表します。

# 引数

  * `N`: (`::Int64`) 取得したサンプルの数
  * `T`: (`::Float64`, [`s`]) サンプルを取得するための期間
  * `delay`: (`::Float64`, [`s`]) 取得を開始するための遅延時間
  * `Δf`: (`::Float64`, [`Hz`]) デルタ周波数。RFパルスの位相を補正するためのものです
  * `ϕ`: (`::Float64`, `[rad]`) 位相。RFパルスの位相を補正するためのものです

# 戻り値

  * `adc`: (`::ADC`) ADC構造体

# 例

```julia-repl
julia> adc = ADC(16, 1, 0.1)

julia> seq = Sequence(); seq += adc; plot_seq(seq)
```
