```julia
(1)
function decibel(S :: Union{Real, AbstractArray{T}}) where T<:Real

(2)
function decibel(S1 :: Union{Real, AbstractArray{T}},
            S2 :: Union{Real, AbstractArray{T}}) where T<:Real
```

(1) 測定値 `S` を、または (2) 2 つの測定値 `S1`./`S2` の比をデシベルに変換します。

入力測定値は実数または任意の次元の実数配列です。

配列入力の場合、比率と変換は要素ごとに計算されます。

**例**:

```julia
using FourierAnalysis
v=sinusoidal(3., 1, 128, 256, 0)
s=spectra(v, 128, 256; func=decibel) # dB でスペクトルを計算
s.y # スペクトルを表示

decibel(s.y)

decibel(10.0)

N=abs.(randn(3, 3))
decibel(N)
```
