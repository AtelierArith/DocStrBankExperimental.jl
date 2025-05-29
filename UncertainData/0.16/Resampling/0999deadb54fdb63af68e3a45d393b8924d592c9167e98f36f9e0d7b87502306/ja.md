```
resample(uv::AbstractUncertainValue, constraint::TruncateMaximum, n::Int)
```

最初に値を表す分布をある最小値で切り捨ててから、再サンプリングを行います。

## 例

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateMaximum(1.1) # 1.1より大きい値は受け入れない

# 分布を切り捨ててから、不確実な値を再サンプリングします。
# 新しい分布を1000回再サンプリングします。
resample(uncertainval, constraint, 1000)
```
