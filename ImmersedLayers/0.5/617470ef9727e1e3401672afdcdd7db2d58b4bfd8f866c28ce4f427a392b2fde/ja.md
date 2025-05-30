```
SurfaceScalarCache(X::VectorData,g::PhysicalGrid[,ddftype=CartesianGrids.Yang3][,scaling=GridScaling])
```

スカラーデータに対する浸漬層操作で使用するための演算子とストレージデータを保持する`BasicILMCache`タイプのキャッシュを作成します。`X`は浸漬された表面セグメントの端点を保持していると仮定され、`g`は物理グリッドです。
