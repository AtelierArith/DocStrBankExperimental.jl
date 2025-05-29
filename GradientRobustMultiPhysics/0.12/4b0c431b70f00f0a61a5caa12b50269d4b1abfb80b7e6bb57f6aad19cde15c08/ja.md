```
mutable struct PDEDescription
    name::String
    equation_names::Array{String,1}
    unknown_names::Array{String,1}
    variables::Array{Array{String,1},1}
    algebraic_constraint::Array{Bool,1}
    LHS::Array{Array{AbstractPDEOperator,1},2}
    RHS::Array{Array{AbstractPDEOperator,1},1}
    BoundaryOperators::Array{BoundaryOperator,1}
    GlobalConstraints::Array{AbstractGlobalConstraint,1}
end
```

n個の方程式とn個の未知数を持つPDEシステムを記述する構造体

PDEシステムは以下によって記述されます。

  * その名前
  * 方程式の名前
  * 未知数の名前
  * 未知数のためのアンズァッツとテスト関数の変数
  * 変数は代数的制約に関連していますか？（例：非圧縮CFDにおける圧力、これは時間離散化に影響を与えます）
  * 左辺を記述するArray{AbstractPDEOperator,1}のn x n配列LHS
  * 右辺を記述するArray{AbstractPDEOperator,1}の長さnの配列RHS
  * 各未知数の境界条件を記述するBoundaryOperatorsの長さnの配列
  * 追加のグローバル制約を記述するGlobalConstraintsの配列

PDEDescriptionは主に二次のn x n行列（LHS）に配置されたPDEOperatorsのセットです。各行列の行は1つの方程式を参照し、PDEOperatorsの配置（例：双線形形式）は、演算子を評価するために使用されるべき未知数の情報を即座に設定します。また、追加の情報が指定される必要がある非線形PDEOperatorsも可能です。UserDataはそのタイプに応じてPDEDescriptionに割り当てられます。演算子の係数はPDEOperatorsに直接（AbstractActionsまたは定数因子の形で）割り当てられ、右辺データはPDEOperatorsの右辺配列（RHS）に割り当てられ、境界データはPDEDescriptionのBoundaryOperatorsに割り当てられます。さらに、グローバルな制約（グローバルゼロ積分平均のようなもの）もGlobalConstraintとして割り当てることができます。
