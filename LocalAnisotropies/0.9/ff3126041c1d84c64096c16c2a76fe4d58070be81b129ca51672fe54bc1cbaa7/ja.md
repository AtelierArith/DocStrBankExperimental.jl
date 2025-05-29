```
LocalKriging(method, localaniso, γ, μ=nothing, localanisohd=nothing)
```

LocalKriging推定ソルバーで、`method`は:MovingWindowsまたは:KernelConvolutionのいずれかです。`γ`は変動モデルで、`μ`は単純クリギングが使用される場合の平均です。`localanisohd`は:KernelConvolutionの場合にのみ必要であり、指定されていない場合は`localaniso`からNNを介して自動的に渡されます。
