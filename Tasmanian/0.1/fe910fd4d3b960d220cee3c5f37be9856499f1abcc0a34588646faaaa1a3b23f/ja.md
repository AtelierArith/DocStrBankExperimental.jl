```
setHierarchicalCoefficients!(tsg::TasmanianSG, coefficients)
```

ローカル多項式、ウェーブレット、およびシーケンスグリッドは、読み込まれた値に基づいて階層係数を使用して近似を構築します。この関数は逆のことを行い、階層係数が直接読み込まれ、値が係数に基づいて計算されます。係数は、例えば、最小二乗法または圧縮センシング問題を解くことによって計算できます。min || A c - f || ここで、AはevaluateHierarchicalFunctions()またはevaluateSparseHierarchicalFunctions()によって返される行列で、xのセットに対するものであり、fはx点でのターゲット関数の値であり、cは対応する階層係数を持つベクトルです。

保留中のリファインメントがある場合、すなわちgetNumLoaded() != 0およびgetNumNeeded() != 0の場合、リファインメントは破棄されます（古い値に基づいて計算されたため、現在は無効です）。

coefficients: getNumOutputs() x getNumPoints()の次元を持つ行列で、各列は対応する点での係数の値に対応します。順序と先頭次元はgetPoints()から得られた点と一致し、evaluateHierarchicalFunctions()の第二次元と同じ順序である必要があります。この行列は、フーリエグリッドを使用する場合、Matrix{ComplexF64}型でなければなりません。
