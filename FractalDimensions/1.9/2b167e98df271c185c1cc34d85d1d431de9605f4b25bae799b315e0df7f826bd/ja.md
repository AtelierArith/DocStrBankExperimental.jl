```
extremevaltheory_dims_persistences(x::AbstractStateSpaceSet, est; kwargs...)
```

与えられた集合内の各点に対して、極値理論に従ってローカル次元 `Δloc` と持続性 `θloc` を返します [Lucarini2016](@cite)。`est` のタイプが次元を計算する際に使用するアプローチを決定します。使用可能な推定器は次のとおりです：

  * [`BlockMaxima`](@ref)
  * [`Exceedances`](@ref)

計算は利用可能なスレッド (`Threads.nthreads()`) に並列化されます。

結果に対する信頼性を得るために、[`extremevaltheory_gpdfit_pvalues`](@ref) も参照してください。

## キーワード引数

  * `show_progress = true`: 進行状況バーを表示します。
  * `compute_persistence = true:` ローカル持続性 `θloc`（極値指標とも呼ばれる）を計算するかどうか。`false` の場合、`θloc` は `NaN` になります。
