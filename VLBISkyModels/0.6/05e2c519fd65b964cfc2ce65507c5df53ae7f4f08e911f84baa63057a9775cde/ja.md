```julia
struct FFTAlg{T} <: VLBISkyModels.FourierTransform
```

モデルの近似数値可視性マップを計算するためにFFTを使用します。DTFTについては[`DFTAlg`](@ref DFTAlg)を、NFFTについては[`NFFTAlg`](@ref NFFTAlg)を参照してください。

# フィールド

  * `padfac`: 画像をパディングする量。実際には小さな素因数を使用するために切り上げます。
  * `flags`: 変換のためのFFTWフラグまたは知恵。デフォルトは`FFTW.ESTIMATE`ですが、サンプルFFTを複数回評価する予定がある場合は、より良いパフォーマンスのために`FFTW.MEASURE`を使用できます。
