```
resample(uv::AbstractUncertainValue, constraint::TruncateUpperQuantile, n::Int)
```

最初に値を表す分布を上位分位点で切り捨て、その後再サンプリングを行うことで再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateUpperQuantile(0.8)

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を1000回再サンプリングします。
resample(uncertainval, constraint, 1000)
```
