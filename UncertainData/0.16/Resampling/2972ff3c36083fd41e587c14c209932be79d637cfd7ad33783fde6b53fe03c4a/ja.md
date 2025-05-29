```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateQuantiles,
    n::Int)
```

`uv`を再サンプリングするには、まず分布のカーネル密度推定をトランケートし、ある分位範囲で上限と下限の両方を提供し、その後`n`回再サンプリングします。

## 例

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateQuantiles(0.1, 0.9)

# 不確実な値を再サンプリングするには、分布をトランケートし、
# 新しい分布を500回再サンプリングします。
resample(uncertainval, constraint, 500)
```
