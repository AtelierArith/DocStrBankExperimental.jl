```
resample(uv::AbstractUncertainValue, constraint::TruncateQuantiles)
```

値を表す分布を一連の分位点で切り捨てた後、再サンプリングを行うことで再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 1, Uniform)
constraint = TruncateLowerQuantile(0.2)

# 分布を切り捨ててから不確実な値を再サンプリングし、
# 新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
