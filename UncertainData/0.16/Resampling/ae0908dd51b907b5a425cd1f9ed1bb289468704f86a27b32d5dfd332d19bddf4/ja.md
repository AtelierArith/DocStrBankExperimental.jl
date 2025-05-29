```
resample(uv::AbstractUncertainValue, constraint::TruncateRange, n::Int)
```

最初に値をある最小値で切り捨ててから、再サンプリングを行うことによって再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateRange(-0.7, 1.1) # 値は範囲[-0.7, 1.1]のみに制限されます

# 不確実な値を`1000`回再サンプリングします。分布を切り捨てた後、
# 新しい分布を`1000`回再サンプリングします
resample(uncertainval, constraint, 1000)
```
