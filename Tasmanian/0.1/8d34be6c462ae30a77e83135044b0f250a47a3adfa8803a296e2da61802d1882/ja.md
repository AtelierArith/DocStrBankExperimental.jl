```
setAnisotropicRefinement!(tsg::TasmanianSG, type, min_growth, output, level_limits = Vector{Int32}(undef, 0))
```

現在読み込まれている点のセットから異方性係数を推定し、推定に基づいて最良の点でグリッドを更新します。

type: 使用する推定を識別する文字列（マニュアルを参照）       推奨: 'iptotal'   'ipcurved'

min_growth: int (正の値)             新しいグリッドに含める新しい点の最小数

output: int (使用する出力を示す) 精緻化に使用する出力を選択         シーケンスグリッドでは、-1を指定するとすべての出力を使用することを示します。

level_limits: (空でない場合) 現在設定されている制限を上書きするために使用されます。制限は空であるか、getNumDimensions()のサイズを持っている必要があります; 空の場合、現在の制限セットが使用されます。
