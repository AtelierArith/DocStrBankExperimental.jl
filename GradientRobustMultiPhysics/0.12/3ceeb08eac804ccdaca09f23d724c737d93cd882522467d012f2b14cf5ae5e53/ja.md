```
function PointEvaluator(FEB::FEVectorBlock, FEOP::AbstractFunctionOperator, action::AbstractAction = NoAction(); AT = ON_CELLS)
```

PointEvaluatorのコンストラクタは、指定された演算子（アクションによって後処理される可能性がある）を使用して、与えられたアセンブリタイプのエンティティ内の任意の点で指定されたFEVectorBlockを評価します。
