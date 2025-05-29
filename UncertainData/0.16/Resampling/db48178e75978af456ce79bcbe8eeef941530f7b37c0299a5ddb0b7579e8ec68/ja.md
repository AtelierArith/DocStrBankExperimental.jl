```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateUpperQuantile)
```

`uv`を再サンプリングするには、まず分布のカーネル密度推定を上限分位点で切り捨て、その後一度再サンプリングします。

## 例

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateUpperQuantile(0.78)

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
