```
abstract type RBOperator{O} <: ParamOperator{O,SplitDomains} end
```

定常アプリケーションにおける縮小順序モデリングフレームワーク内で使用される縮小代数演算子を表す型です。RBOperatorは以下の情報を含むべきです：

  * [`reduced_spaces`](@ref) に従って計算された縮小テストおよび試行空間
  * [`reduced_weak_form`](@ref) に従って計算されたハイパー縮小残差およびヤコビ行列

サブタイプ：

  * [`GenericRBOperator`](@ref)
  * [`LinearNonlinearRBOperator`](@ref)
