```julia
plot_tmrcas(arg; width, npoints, noprogress, kwargs...)

```

最近共通祖先までの時間の階段プロット。追加のキーワード引数は直接[`UnicodePlots.histogram`](@ref)に渡されます。

この関数は実際には各再結合ブレークポイントのtmrcaを計算しますが、これは**非常に**要求が厳しく、グラフのシミュレーションよりもはるかに多くの計算を必要とします。計算時間を短縮するためにマルチスレッドで実行されます。

また、[`tmrca`](@ref)も参照してください。

# キーワード

  * `npoints` (`nrecombinations(arg) + 1`): TMRCAを計算するためのポイントの近似数。デフォルトでは、すべての再結合ブレークポイントが考慮されます。計算時間を短縮するために、ポイントの数を少なくしてください。
  * `width` (`76`): プロットの幅。デフォルトの最大値76は、80列幅のプロットを生成します。
  * `noprogress` (`false`): 進行状況メーターを非表示にします。
  * `kwargs...`: 追加のキーワード引数は直接[`UnicodePlots.histogram`](https://github.com/JuliaPlots/UnicodePlots.jl)に渡されます。
