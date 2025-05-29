StochasticProfileLikelihood(DM::AbstractDataModel, C::HyperCube=Domain(DM); TargetTime=60, Nsingle::Int=5, N::Int=Nsingle^length(C), nbins::Int=4Nsingle, parallel::Bool=true, maxval::Real=1e5, DoBiLog::Bool=true, kwargs...) は、パラメータ空間にわたる尤度をサンプリングし、各パラメータの値範囲をビンに分割し、すべてのサンプルからこのビン内のそれぞれのパラメータ値に対する最良の観測尤度値を視覚化します。したがって、これはプロファイル尤度の粗いグローバル近似を提供し、`N` ⟶ ∞ の大サンプル制限で真のプロファイル尤度に近づきますが、ニuisanceパラメータの再最適化が必要ないため、計算コストははるかに安価です。これにより、最適化を開始するための初期パラメータ値の良い候補に関するヒントを得ることができ、逆に、常に不適切な尤度値のためにマルチスタートフィッティングから除外できるパラメータ範囲の部分を示すこともできます。

このサンプリングの結果は、`MultistartResults`オブジェクトの`FinalPoints`および`FinalObjectives`フィールドに保存されます。

`TargetTime`キーワード引数は、サンプリングが約指定された時間（秒）を必要とすることが期待されるようにサンプル数を選択するために使用できます。
