```
plan_rfft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

最適化された実数入力FFTを事前に計画します。これは、[`fft`](@ref)の代わりに[`rfft`](@ref)を使用する点を除いて、[`plan_fft`](@ref)に似ています。最初の2つの引数と変換結果のサイズは、[`rfft`](@ref)と同じです。
