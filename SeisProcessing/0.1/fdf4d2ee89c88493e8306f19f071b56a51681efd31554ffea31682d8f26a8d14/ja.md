```
SeisAddNoise(d, snr; <キーワード引数>)
```

N次元の入力データ `d` にノイズを追加します。信号対ノイズ比レベル `snr` を指定する必要があります。ノイズはキーワード `L` を使用してバンド制限できます。

# 引数

  * `d::Array{Real, N}`: N次元データ。
  * `snr::Real`: 信号対ノイズ比。
  * `db::Bool=false`: snr が振幅で与えられる場合、フラグは false です。snr が dB で与えられる場合、フラグは true です。
  * `pdf::AbstractString="gaussian"`: ランダムノイズの確率分布:

`"gaussian"` または `"uniform"`。

  * `L::Int=1`: ランダムノイズをバンド制限するための平均化演算子の長さ。

# 例

```julia
julia> using PyPlot
julia> w = Ricker(); wn = SeisAddNoise(w, 2); plot(w); plot(wn);
MeasureSNR(w, wn)
julia> d = SeisHypEvents(); dn = SeisAddNoise(d, 1.0, db=true, L=9);
SeisPlotTX([d dn]); MeasureSNR(d, dn, db=true)
```

クレジット: Juan I. Sabbione, 2016 ```
