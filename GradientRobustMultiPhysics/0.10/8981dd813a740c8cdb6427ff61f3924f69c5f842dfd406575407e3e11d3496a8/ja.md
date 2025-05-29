```julia
abstract type DofMap <: ExtendableGrids.AbstractGridAdjacency
```

Dofmapは有限要素空間のExtendableGrids.AbstractGridAdjacencyとして保存され、異なるAssemblyTypesに関する情報を収集します。これらは必要に応じて自動的に生成され、各サブタイプに関連付けられたdofmapはFESpace[DofMap]を介してアクセスできます。
