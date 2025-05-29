```
struct LinearNonlinearParamFEOperator{O<:UnEvalOperatorType,T<:TriangulationStyle} <: ParamFEOperator{O,T}
  op_linear::ParamFEOperator
  op_nonlinear::ParamFEOperator
end
```

非線形問題における線形性に応じた項の分離を考慮するインターフェース。これにより、線形残差/ヤコビ行列を一度だけ構築して保存し、ニュートン様の反復では非線形成分のみを評価して組み立てることができます。
