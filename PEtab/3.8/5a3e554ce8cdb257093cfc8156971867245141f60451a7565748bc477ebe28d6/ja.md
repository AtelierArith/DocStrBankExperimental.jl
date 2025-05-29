```
get_startguesses(prob::PEtabODEProblem, n::Integer; kwargs...)
```

`prob`内のパラメータ境界内で`n`個のランダムパラメータベクトルを生成します。

`n = 1`の場合、単一のランダムベクトルが返されます。`n > 1`の場合、ランダムパラメータベクトルのベクトルが返されます。いずれの場合も、パラメータベクトルは`ComponentArray`として返されます。`ComponentArray`とのインタラクションの詳細については、ドキュメントおよびComponentArrays.jlの[ドキュメント](https://github.com/jonniedie/ComponentArrays.jl)を参照してください。

また、[`calibrate`](@ref)および[`calibrate_multistart`](@ref)も参照してください。

## キーワード引数

  * `sampling_method = LatinHypercubeSample()`: 多様（広がった）なパラメータベクトルのセットをサンプリングするための方法。 [QuasiMonteCarlo](https://github.com/SciML/QuasiMonteCarlo.jl)の任意のアルゴリズムが許可されていますが、通常は良好なパフォーマンスを発揮するため、デフォルトの`LatinHypercubeSample`が推奨されます。
  * `sample_prior::Bool = true`: パラメータに事前分布がある場合、事前分布からランダムなパラメータ値をサンプリングするかどうか。
  * `allow_inf::Bool = false`: 尤度を計算できないパラメータベクトルを返すかどうか（通常、`ODEProblem`が解決できないために発生します）。パラメータ推定のためには、計算可能な尤度を持つスタートポイントを使用することが一般的に意味があるため、このオプションを変更することは通常意味がありません。
