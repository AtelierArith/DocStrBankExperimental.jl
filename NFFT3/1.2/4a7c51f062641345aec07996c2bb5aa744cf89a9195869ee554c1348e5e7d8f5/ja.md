```
nfft_get_LinearMap(N::Vector{Int}, X::Array{Float64}; n, m::Integer, f1::UInt32, f2::UInt32)::LinearMap
```

は、NFFTを計算する線形マップを提供します。

# 入力

  * `N` - 三角多項式 $f$ の多重帯域制限 $(N_1, N_2, \ldots, N_D)$。
  * `X` - ノード X。
  * `n` - 次元ごとのオーバーサンプリング $(n_1, n_2, \ldots, n_D)$。
  * `m` - ウィンドウサイズ。大きな m はより高い精度をもたらしますが、計算コストも高くなります。
  * `f1` - NFFT フラグ。
  * `f2` - FFTW フラグ。

# 参照

[`NFFT{D}`](@ref)
