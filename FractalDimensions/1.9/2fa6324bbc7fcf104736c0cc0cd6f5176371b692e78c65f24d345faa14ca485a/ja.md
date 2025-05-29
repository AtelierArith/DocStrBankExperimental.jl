```
slopefit(x, y [, t::SLopeFit]; kw...) → s, s05, s95
```

2つの `AbstractVectors` `y` と `x` の曲線における線形スケーリング領域を `t` を推定方法として使用してフィットします。推定された傾きと、その信頼区間を返します。

推定に使用できる `t` の方法は次のとおりです：

  * [`LinearRegression`](@ref)
  * [`LargestLinearRegion`](@ref) (デフォルト)
  * [`AllSlopesDistribution`](@ref)

キーワード `ignore_saturation = true` は、曲線 `y(x)` の開始時と終了時に（時々）発生する飽和を無視します。ここでは曲線が平坦になります。キーワード `sat_threshold = 0.01` は、飽和が何であるかを決定します：`abs(y[i]-y[i+1]) < sat_threshold` の間、私たちは飽和領域にいます。言い換えれば、値 `sat_threshold/dx` の傾きは無視され、ここで `dx = x[i+1] - x[i]` です。

キーワード `ci = 0.95` は、信頼区間の値が返される量子（および 1 - 量子）を指定し、デフォルトでは 95%（したがって 5%）です。
