```
plan_bfft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

[`plan_fft`](@ref) と同様ですが、正規化されていない逆変換 [`bfft`](@ref) を実行するプランを生成します。
