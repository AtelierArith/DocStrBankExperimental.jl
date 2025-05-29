```
barrier_iterations(model::Model)
```

最近の最適化中の累積バリア反復回数を取得します。

ソルバーは、この関数を使用するために `MOI.BarrierIterations()` を実装する必要があります。
