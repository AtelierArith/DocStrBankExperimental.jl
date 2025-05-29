```
resample(uv::AbstractUncertainValue, constraint::TruncateMinimum)
```

最小値で分布を切り捨てた後、再サンプリングを行うことによって再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateMinimum(-0.5) # -0.5未満の値は受け入れない

# 分布を切り捨ててから不確実な値を再サンプリングし、
# 新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
