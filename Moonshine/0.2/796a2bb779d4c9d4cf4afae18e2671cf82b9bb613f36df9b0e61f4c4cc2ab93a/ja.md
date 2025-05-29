```julia
plot_breakpoints(arg; nbins, height, kwargs...)

```

再結合イベントの位置のヒートマップ。

参照してください [`breakpoints`](@ref)

# キーワード

  * `nbins` (`clamp(nrecombinations(arg) ÷ 100, 1, 69)`): ビンの数。デフォルトの最大値69は、80列幅のきれいなプロットを生成します。
  * `height` (`7`): プロットの高さ。
  * `kwargs...`: 追加のキーワード引数は、直接 [`UnicodePlots.histogram`](https://github.com/JuliaPlots/UnicodePlots.jl) に渡されます。
