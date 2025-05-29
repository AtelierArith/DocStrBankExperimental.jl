```
resample(uv::AbstractUncertainValue, constraint::TruncateUpperQuantile)
```

上位分位数で値を表す分布を最初に切り捨ててから、再サンプリングを行います。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateUpperQuantile(0.8)

# 分布を切り捨ててから不確実な値を再サンプリングし、
# 新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
