```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateMinimum)
```

最小値で値を提供する分布のカーネル密度推定を最初に切り捨ててから、`uv`を再サンプリングします。

## 例

```julia
# 平均 = 0、標準偏差 = 1の正規分布で表される不確実な値。
uncertainval = UncertainValue(rand(Normal(0, 1), 1000))

constraint = TruncateMinimum(0.2) # 0.2未満の値は受け入れない

# 分布を切り捨ててから、不確実な値を再サンプリングし、
# 新しい分布を700回再サンプリングします。
resample(uncertainval, constraint, 700)
```
