```
abstract type ParamFEOperator{O<:UnEvalOperatorType,T<:TriangulationStyle} <: FEOperator end
```

[`Gridap`](@ref) における `FEOperator` のパラメトリック拡張。標準の FEOperator と比較して、以下の新機能があります：

  * ParamSpace が提供されており、パラメトリックな実現を ParamFEOperator から直接抽出できます
  * 望ましいノルムにおける誤差を自動的に計算できるように、ノルム行列を表す関数が提供されています

サブタイプ：

  * [`ParamFEOpFromWeakForm`](@ref)
  * [`LinearNonlinearParamFEOperator`](@ref)
  * [`TransientParamFEOperator`](@ref)
