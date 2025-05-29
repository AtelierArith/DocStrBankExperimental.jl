```julia
mutable struct LinearizationProblem{F<:ModelingToolkit.LinearizationFunction, T}
```

線形化操作を表す構造体です。ループ内で複数の線形化のために動作点を効率的に更新するために、象徴的にインデックス付けできます。この構造体の`.t`フィールドを変更することで、独立変数の値を設定できます。
