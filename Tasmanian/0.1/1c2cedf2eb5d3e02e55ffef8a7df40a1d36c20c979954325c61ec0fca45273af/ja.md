```
evaluateSparseHierarchicalFunctions(tsg::TasmanianSG, x)
```

は、ドメイン内の一連の点で階層関数を評価します。この関数と evaluateHierarchicalFunctions() の違いは、返される結果のタイプ、すなわちスパース行列と密行列にあります。

この関数の動機は、ローカル多項式およびウェーブレットグリッドが通常スパース行列を生成するためです。

x: getNumDimensions() 行と NumX 列を持つ行列       エントリは評価するための点を示します。

output: TasmanianSimpleSparseMatrix クラスを返します         これは、aPntr、aIndx、および aVals の3つのフィールドを持つシンプルなクラスで、         それぞれの型は numpy.ndarray で、         int32、int32、および float64 です。         NumRows と NumCols はメタフィールドで、値は         NumRows = x.shape[0]         NumCols = getNumPoints() です。         スパース行列は x.shape[0]         次元に沿って圧縮されており、すなわち列圧縮形式を使用しています。
