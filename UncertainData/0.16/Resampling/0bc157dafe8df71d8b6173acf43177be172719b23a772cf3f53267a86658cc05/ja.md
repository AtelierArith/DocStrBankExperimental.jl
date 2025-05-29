```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateUpperQuantile)
```

`uv`を再サンプリングするには、まず分布のカーネル密度推定をある分位範囲で上限と下限の両方で切り捨ててから、1回再サンプリングします。

## 例

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateQuantiles(0.1, 0.9)

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を1回再サンプリングします。
resample(uncertainval, constraint)
```
