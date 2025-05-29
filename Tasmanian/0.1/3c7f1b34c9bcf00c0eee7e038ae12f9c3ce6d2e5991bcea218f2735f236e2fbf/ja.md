```
removePointsByHierarchicalCoefficient!(tsg::TasmanianSG, tolerance, output = -1, scale_correction = [], NumKeep = -1)
```

は、トレランスを超える相対的な余剰を持つグリッド内のポイントを削除するか、最も大きな余剰を持つポイントのセット数を保持します。

tolerance: float (positive)            相対的な余剰のトレランス、すなわち、            トレランスを超える余剰に関連付けられたポイントのみを保持します。            NumKeepが正の場合、トレランスは無視されます。

output: int (使用する出力を示す)         考慮する出力を選択します。         -1を受け入れてすべての出力を示します。

scale_correction: ベクトルまたは行列                   output = -1でgetNumOutputs() > 1の場合、                   その場合、形状が                   getNumOutputs() X getNumLoaded()の行列を使用し、                   階層係数ごとに1つの重みを持ちます。                   output > -1の場合、ポイントごとに1つの重みを持つ                   ベクトルを使用します。

NumKeep: int (positiveまたは-1と等しい)          保持するポイントの数を示します。          -1に設定されている場合、トレランスがカットオフとして使用されます。          正の場合、指定された数のポイントが保持されます。
