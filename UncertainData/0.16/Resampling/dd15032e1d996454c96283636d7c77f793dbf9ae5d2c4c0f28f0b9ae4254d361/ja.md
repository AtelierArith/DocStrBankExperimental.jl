```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateMaximum, n::Int)
```

`uv`を再サンプリングします。まず、分布のカーネル密度推定をある最小値で切り捨て、その後`n`回再サンプリングします。

## 例

```julia
# 平均 = 0、標準偏差 = 1の正規分布で表される不確実な値。
uncertainval = UncertainValue(rand(Normal(0, 1), 1000))

constraint = TruncateMaximum(0.8) # 1.1より大きい値は受け入れない

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を700回再サンプリングします。
resample(uncertainval, constraint, 700)
```
