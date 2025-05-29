```
MeasureSNR(signal, noisy; db=false)
```

クリーンな入力 `signal` と汚染された入力 `noisy` の間の信号対雑音比を測定します。

# 引数

  * `signal::Array{Real, N}`: N次元のクリーン信号。`N` は <= 5 でなければなりません。
  * `noisy::Array{Real, N}`: `signal` と同じサイズの N次元のノイズ信号。
  * `db::Bool=false`: 信号対雑音比が振幅で測定される場合、フラグは false です。snr が dB の場合、フラグは true です。

# 例

```julia
julia> d = SeisHypEvents(); dnoisy = SeisAddNoise(d, 2);
MeasureSNR(d, dnoisy)
```
