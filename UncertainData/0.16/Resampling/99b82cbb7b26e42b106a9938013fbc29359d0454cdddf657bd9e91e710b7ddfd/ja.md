```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateUpperQuantile,
    n::Int)
```

`uv`を再サンプリングするには、まず分布が提供する上位分位点での値のカーネル密度推定を超えて切り捨て、その後`n`回再サンプリングします。

## 例

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateLowerQuantile(0.16)

# 分布を切り捨てて不確実な値を再サンプリングし、
# 新しい分布を500回再サンプリングします。
resample(uncertainval, constraint, 500)
```
