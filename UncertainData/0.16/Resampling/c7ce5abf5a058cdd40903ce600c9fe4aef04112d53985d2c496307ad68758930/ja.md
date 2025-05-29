```
resample(uv::AbstractUncertainValue, constraint::TruncateStd, n::Int; 
    n_draws::Int = 10000)
```

値を表す分布を平均の周りの標準偏差のいくつか倍に切り捨てることによって再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateStd(1.1) # 平均の周りの1.1*標準偏差の範囲内の値のみを受け入れる

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を1000回再サンプリングします。
resample(uncertainval, constraint, 1000)
```
