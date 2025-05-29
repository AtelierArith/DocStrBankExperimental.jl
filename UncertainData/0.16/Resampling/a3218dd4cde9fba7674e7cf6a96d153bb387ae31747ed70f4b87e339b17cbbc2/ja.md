```
resample(uv::AbstractUncertainValue, constraint::NoConstraint, n::Int)
```

制約なしで不確実な値を再サンプリングします（完全な供給分布を使用します）。

## 例

```julia
uncertainval = UncertainValue(0, 0.2, Normal)

# 完全な分布を1000回再サンプリングして不確実な値を再サンプリングします。
resample(uncertainval, NoConstraint(), 1000)
```
