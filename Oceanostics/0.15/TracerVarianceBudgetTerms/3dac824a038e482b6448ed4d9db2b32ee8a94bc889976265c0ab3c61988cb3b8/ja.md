```julia
TracerVarianceDiffusiveTerm(model, tracer_name; location)

```

トレーサー分散予測方程式の拡散項を計算する `KernelFunctionOperation` を返します。これは、Oceananigans の拡散トレーサーフラックス発散カーネルを使用します：

```
    DIFF = 2 c ∂ⱼFⱼ
```

ここで `c` はトレーサーであり、`Fⱼ` は `j` 番目の方向におけるトレーサーの拡散フラックスです。

```julia
grid = RectilinearGrid(size=(4, 4, 4), extent=(1, 1, 1))
model = NonhydrostaticModel(grid=grid, tracers=:b, closure=SmagorinskyLilly())

DIFF = TracerVarianceDiffusiveTerm(model, :b)
```
