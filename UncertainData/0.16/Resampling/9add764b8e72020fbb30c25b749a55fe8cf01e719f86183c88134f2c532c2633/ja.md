```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateLowerQuantile)
```

`uv`を再サンプリングするには、まず分布が提供する値のいくつかの下位分位点でのカーネル密度推定を下回る部分を切り捨て、その後一度再サンプリングします。

## 例

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateLowerQuantile(0.16)

# 分布を切り捨てて不確実な値を再サンプリングし、
# その後新しい分布を一度再サンプリングします。
resample(uncertainval, constraint)
```
