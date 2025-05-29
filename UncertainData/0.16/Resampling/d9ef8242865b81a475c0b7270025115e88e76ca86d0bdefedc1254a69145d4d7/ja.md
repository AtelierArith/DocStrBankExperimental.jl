```
resample(uv::AbstractUncertainValue, constraint::TruncateRange)
```

最初に値を表す分布をある最小値で切り捨ててから、再サンプリングを行うことで再サンプリングします。

## 例

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateRange(-0.7, 1.1) # 値は範囲[-0.7, 1.1]のみに制限されます

# 分布を切り捨ててから、不確実な値を再サンプリングします。
# その後、新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
