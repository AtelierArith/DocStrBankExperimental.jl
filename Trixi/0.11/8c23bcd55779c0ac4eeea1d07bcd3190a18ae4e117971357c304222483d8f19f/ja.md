```
PlotData1D(sol; kwargs...)
```

`OrdinaryDiffEq.solve!`（`SciMLBase.ODESolution`を返す）またはTrixi.jlの独自の`solve!`（`TimeIntegratorSolution`を返す）によって作成された解オブジェクトから`PlotData1D`オブジェクトを作成します。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

