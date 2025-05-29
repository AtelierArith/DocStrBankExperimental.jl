```
plan_brfft(A, d [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

最適化された実数入力の非正規化変換を事前に計画します。これは、[`rfft`](@ref)の代わりに[`brfft`](@ref)を使用する[`plan_rfft`](@ref)に似ています。最初の2つの引数と変換結果のサイズは、[`brfft`](@ref)と同じです。
