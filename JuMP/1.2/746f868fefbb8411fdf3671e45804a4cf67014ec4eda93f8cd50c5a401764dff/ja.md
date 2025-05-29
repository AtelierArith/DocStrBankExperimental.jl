```
simplex_iterations(model::Model)
```

最近の最適化中の単体法の累積反復回数を取得します。

ソルバーは、この関数を使用するために `MOI.SimplexIterations()` を実装する必要があります。
