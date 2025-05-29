```
const TransientParamFEOperator{O<:ODEParamOperatorType,T<:TriangulationStyle} = ParamFEOperator{O,T}
```

[`Gridap`](@ref) における `TransientFEOperator` のパラメトリック拡張です。標準の TransientFEOperator と比較して、以下の新機能があります：

  * パラメトリックな実現を `TransientParamFEOperator` から直接抽出できるように [`TransientParamSpace`](@ref) が提供されています
  * 所望のノルムにおける誤差を自動的に計算できるように、ノルム行列を表す関数が提供されています

サブタイプ：

  * [`TransientParamFEOpFromWeakForm`](@ref)
  * [`TransientParamLinearFEOpFromWeakForm`](@ref)
