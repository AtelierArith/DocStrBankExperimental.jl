```
SurfaceScalarCache(body::Body/BodyList,g::PhysicalGrid[,ddftype=CartesianGrids.Yang3][,scaling=GridScaling])
```

スカラーデータに対する浸漬層操作で使用する演算子とストレージデータを保持するタイプ `BasicILMCache` のキャッシュを作成します。これは、直接ではなく `ILMSystem` 内から呼び出されることがあります。

`body` は `Body` または `BodyList` のタイプであることができます。キーワード `scaling` は、操作のスケーリングを設定するために使用できます。デフォルトでは、これは `IndexScaling` に設定されており、正則化と補間が対称行列になるように設定されます（すなわち、補間はベクトルの内積に関して正則化の随伴であり、グリッド上のベクトル解析操作は単純な差分です）。`scaling = GridScaling` を使用すると、グリッドとポイントの間隔が考慮されます。補間と正則化は、離散化された表面および体積積分に基づく内積に関して随伴であり、ベクトル解析操作はグリッド間隔によってスケーリングされます。
