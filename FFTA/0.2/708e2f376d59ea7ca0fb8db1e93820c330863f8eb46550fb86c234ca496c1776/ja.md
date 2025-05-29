```julia
fft!(
    out::AbstractArray{T, 1},
    in::AbstractArray{U, 1},
    start_out::Int64,
    start_in::Int64,
    d::FFTA.Direction,
    _::FFTA.CompositeFFT,
    g::FFTA.CallGraph{T},
    idx::Int64
)

```

クーリー・タキー合成FFT、事前に計算されたコールグラフを使用

# 引数

`out`: 出力ベクトル `in`: 入力ベクトル `start_out`: 出力ベクトルの最初の要素のインデックス `start_in`: 入力ベクトルの最初の要素のインデックス `d`: 変換の方向 `g`: この変換のコールグラフ `idx`: コールグラフ内の現在の変換のインデックス
