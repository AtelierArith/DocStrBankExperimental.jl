```julia
solve(
    prob::Union{HighDimPDE.PIDEProblem, HighDimPDE.ParabolicPDEProblem},
    alg::HighDimPDE.DeepSplitting,
    dt;
    batch_size,
    abstol,
    verbose,
    maxiters,
    use_cuda,
    cuda_device,
    verbose_rate
) -> HighDimPDE.PIDESolution{_A, _B, _C, Vector{T}, Vector{Any}, Nothing} where {_A, _B, _C, T}

```

`PIDESolution`オブジェクトを返します。

# 引数

  * `maxiters`: 時間ステップごとの反復回数。タプルで指定でき、`maxiters[1]`は最初の時間ステップで使用されるニューラルネットワークのトレーニングに使用され（長くなる可能性があります）、`maxiters[2]`は残りの時間ステップで使用されます。
  * `batch_size` : バッチサイズ。
  * `abstol` : トレーニングが停止される目的関数の閾値。
  * `verbose` : トレーニング情報を印刷します。
  * `verbose_rate` : トレーニング情報を印刷するレート（毎`verbose_rate`反復）。
  * `use_cuda` : CUDAを使用するには`true`に設定します。
  * `cuda_device` : 整数で、`use_cuda == true`の場合にトレーニングで使用されるCUDAデバイスを設定します。
