```
function FEEvaluator(FE::FESpace, operator::AbstractFunctionOperator, qrule::QuadratureRule; T = Float64, AT = ON_CELLS, L2G = nothing)
```

指定されたFESpace、演算子、および指定されたQuadratureRuleの四分点での有限要素基底関数評価を処理するFEEvaluatorを構築します。新しいセルに入る際に評価を更新するためのupdate!関数があります。評価はFEEvaluator.cvals[j,k,i]を介してアクセスでき、ここでiは四分点ID、kはローカル自由度番号、jはコンポーネントです。

行列値演算子の評価、例えばGradientの場合は、長いベクトル（コンポーネント順）として提供されることに注意してください。
