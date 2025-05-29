```
RCPair{T<:AbstractFloat}(undef, realsize::Dims, dims=1:length(realsize))
```

実数値データに対してインプレースのフーリエ変換（および逆変換）を行うためのバッファを作成します。単一の基盤バッファは、実データまたは複素データとして見ることができます：

```julia
RC = RCpair{Float64}(undef, (10, 10))
real(RC) # 10×10 実配列
complex(RC) # 6×10 複素配列
```

`dims` は、どの次元が変換されるかを制御するために使用できます。

ユーザーはバッファの現在の状態を追跡する責任があります：

```julia
copy!(RC, rand(10, 10))   # 実数値データをバッファにコピーします； `real(RC)` が関連するビューです
rfft!(RC)                 # 実数値データのFFTを計算します；今や `complex(RC)` が関連するビューです
irfft!(RC)                # 複素値データの逆FFTを計算します；今や `real(RC)` が関連するビューです
```
