```
resample(uv::AbstractUncertainValue, constraint::TruncateMinimum, n::Int)
```

最初に値を表す分布をある最小値で切り捨ててから、再サンプリングを行うことで再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateMinimum(-0.5)

# 分布を切り捨ててから、不確実な値を再サンプリングします。
# 新しい分布を1000回再サンプリングします。
resample(uncertainval, constraint, 1000)
```
