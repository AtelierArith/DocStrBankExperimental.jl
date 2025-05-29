```julia
approxDeconv(dfg, fctsym; ...)
approxDeconv(dfg, fctsym, solveKey; retries)

```

因子 `fctsym` の予測測定値を見つけるための一般化された逆畳み込み。予測されたノイズ値の逆解を行い、(新しく予測された値と既知の「測定された」ノイズ) のタプルを返します。

ノート

  * `approxConvBelief` に含まれる逆の操作。
  * 詳細については [`solveFactorMeasurements`](@ref) を参照してください。

関連

[`approxConvBelief`](@ref), `deconvSolveKey`
