依存関係の種類：

  * `fmi2DependencyKindDependent`: 特に構造はなく、f(v)
  * `fmi2DependencyKindConstant`: 定数因子、c*v（実数値変数のみ）
  * `fmi2DependencyKindFixed`: 調整可能な因子、p*v（実数値変数のみ）
  * `fmi2DependencyKindTunable` [ToDo]
  * `fmi2DependencyKindDiscrete` [ToDo]

出典: FMI2.0.3 Spec for fmi2VariableDependency [p.60] 
