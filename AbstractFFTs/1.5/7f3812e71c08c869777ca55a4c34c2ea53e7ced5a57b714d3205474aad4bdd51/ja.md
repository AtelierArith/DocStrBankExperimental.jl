```
plan_irfft(A, d [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

最適化された逆実数入力FFTを事前に計画します。これは[`plan_rfft`](@ref)に似ていますが、[`irfft`](@ref)および[`brfft`](@ref)に対してそれぞれ異なります。最初の3つの引数は[`irfft`](@ref)と同じ意味を持ちます。
