```
resample(uv::AbstractUncertainScalarKDE, constraint::NoConstraint)
```

制約なしで再サンプリング（値を表す全分布を使用）

## 例

```julia
some_sample = rand(Normal(), 1000)

# 数値の単一ベクトルでUncertainValueを呼び出すと、KDE推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

# 全分布を一度再サンプリングすることで不確実な値を再サンプリングします。
resample(uncertainval, NoConstraint())
```
