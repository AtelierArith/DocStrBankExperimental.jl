```
blocking_analysis(v::AbstractVector; α = 0.01, corrected = true, skip=0, warn=true)
-> BlockingResult(mean, err, err_err, p_cov, k, blocks)
```

相関のある時系列のサンプル平均 `mean` を計算し、平均の標準偏差（標準誤差） `err` を推定します。これは、Flyvberg と Peterson のブロッキングアルゴリズム [JCP (1989)](http://aip.scitation.org/doi/10.1063/1.457480) と、Jonsson の M テスト [PRE (2018)](https://link.aps.org/doi/10.1103/PhysRevE.98.043304) を使用して、有意水準 $1-α$ で行われます。

`skip` を使用して、`v` の最初の `skip` 要素をスキップします。 `corrected` は、分散のバイアス補正が使用されるかどうかを制御します。 M テストに従って時系列のデコレートが失敗した場合、標準誤差として `NaN` が返され、 `k` には `-1` が返されます。キーワード引数 `warn` は、警告メッセージがログに記録されるかどうかを制御します。

要約結果は [`BlockingResult`](@ref) として返されます。 `k - 1` は、相関のない時系列に対する仮説検定を通過するために必要なブロッキング変換の数であり、 `err_err` は推定された標準誤差または `err` です。

各リブロッキングステップからの詳細な結果は [`blocking_analysis_data`](@ref) で取得できます。

[`BlockingResult`](@ref)、[`shift_estimator`](@ref)、[`ratio_of_means`](@ref)、[`blocking_analysis_data`](@ref) を参照してください。
