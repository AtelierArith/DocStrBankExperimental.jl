```
sampleplot([x::AbstractVector=f.x, ]f::FiniteGP; samples=1, kwargs...)
```

ガウス過程のプロジェクション `f` と `x` のサンプルをプロットします。

!!! note
    この関数を使用する前に、[Plots.jl](https://github.com/JuliaPlots/Plots.jl) をロードしてください。


複数のサンプルをプロットする場合、これらは *単一* の系列として扱われます（つまり、`label` を提供するときに、凡例には単一のエントリのみが追加されます）。

# 例

```julia
using Plots

gp = GP(SqExponentialKernel())
sampleplot(gp(rand(5)); samples=10, linealpha=1.0)
```

与えられた例は、GP `gp` のプロジェクションから10のサンプルをプロットします。`linealpha` はデフォルトの0.35から1に変更されています。

---

```
sampleplot(x::AbstractVector, gp::AbstractGP; samples=1, kwargs...)
```

有限プロジェクション `gp(x, 1e-9)` と `x` のサンプルをプロットします。
