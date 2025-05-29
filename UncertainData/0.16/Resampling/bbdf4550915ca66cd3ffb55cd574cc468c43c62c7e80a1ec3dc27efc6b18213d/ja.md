```
resample(uv::AbstractUncertainValue, constraint::TruncateUpperQuantile)
```

値を表す分布を下位分位点で切り捨てた後、再サンプリングを行うことで再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateLowerQuantile(0.16)

# 分布を切り捨ててから不確実な値を再サンプリングし、
# 新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
