```
resample(uv::AbstractUncertainScalarKDE, constraint::NoConstraint, n::Int)
```

制約なしで再サンプリング（値を表す全分布を使用）

## 例

```julia
some_sample = rand(Normal(), 1000)

# 単一の数値ベクトルで UncertainValue を呼び出すと、KDE 推定がトリガーされます
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

# 不確実な値をフル分布を n 回再サンプリングすることで再サンプリングします
resample(uncertainval, NoConstraint(), n)
```
