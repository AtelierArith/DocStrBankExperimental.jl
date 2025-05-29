```
SimpleAdaptiveStepper(dx; dtmax = 0.1, dtmin = 1e-10)
```

[`TimeSteppingStrategy`](@ref)を作成し、次の時間ステップを計算するために単純な適応アルゴリズムを使用します。

```
     dt = clamp(dx/vmax, dtmin, dtmax)
```
