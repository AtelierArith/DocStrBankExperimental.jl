```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateRange)
```

`uv`を再サンプリングするには、まず分布のカーネル密度推定を最小値と最大値で切り捨ててから、1回再サンプリングします。

## 例

```julia
# 平均 = 0、標準偏差 = 1の正規分布で表される不確実な値。
uncertainval = UncertainValue(rand(Normal(0, 1), 1000))

# 値は範囲[-0.9, 1.2]の中のみを受け入れる
constraint = TruncateRange(-0.9, 1.2)

# 分布を切り捨ててから、不確実な値を再サンプリングし、
# 新しい分布を300回再サンプリングします。
resample(uncertainval, constraint, 300)
```
