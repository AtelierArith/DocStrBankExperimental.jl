```
ratio_of_means(num, denom; α=0.01, corrected=true, mc_samples=nothing, skip=0, warn=true)
-> r::RatioBlockingResult
```

`num` と `denom` が相関のある時系列であると仮定して、`mean(num)/mean(denom)` の比率を推定します。最初の `skip` 要素をスキップします。ブロッキング分析は m-test を使用して時系列の相関を解除します。詳細は [`blocking_analysis`](@ref) を参照してください。残りの標準誤差と平均の相関は [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) を使用して伝播されます。結果は [`RatioBlockingResult`](@ref) として報告されます。

比率のロバストな推定値は `pmedian(r)` から得られ、信頼区間は `pquantile()` から得られます。例えば、95% 信頼区間のために `pquantile(r, [0.025, 0.975])` を使用します。

線形不確実性伝播からの推定値は `r.f` と `r.σ_f` として返され、[`x_by_y_linear`](@ref) を使用します。標準誤差の推定値 `r.σ_f` は、変動係数 `std(denom)/mean(denom)` が小さい場合にのみ信頼できます: `abs(r.δ_y) < 0.1`。この条件下で比率は正規分布として近似できます。詳細は [wikipedia](https://en.wikipedia.org/wiki/Propagation_of_uncertainty) と [Díaz-Francés, Rubio (2013)](http://link.springer.com/10.1007/s00362-012-0429-2) を参照してください。

キーワード `mc_samples` は、[`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) による誤差伝播に使用されるサンプルの数を制御します。デフォルトには `nothing` を使用し、型に一貫性を持たせてサンプル数を 1000 に設定するには `Val(1000)` を使用します。

キーワード `warn` は、ブロッキングが失敗した場合やノイズの多い分母が遭遇した場合に警告メッセージがログに記録されるかどうかを制御します。

注意: [`RatioBlockingResult`](@ref) に関する統計を計算するには、関数 `pmedian`、`pquantile`、`pmiddle`、`piterate`、`pextrema`、`pminimum`、`pmaximum`、`pmean`、および `pcov` を使用してください。
