```
entropy_wavelet(x; wavelet = Wavelets.WT.Daubechies{12}(), base = 2)
```

ウェーブレットエントロピーを計算します。この関数は単なる便利な呼び出しです：

```julia
est = WaveletOverlap(wavelet)
information(Shannon(base), est, x)
```

詳細については[`WaveletOverlap`](@ref)を参照してください。
