これは、fixed_point関数からの結果を含んでいます。

以下のフィールドが含まれています：

  * `FixedPoint_` - 見つかった固定点を持つ`Vector`。
  * `Other_Output_` - fixedpoint関数の他の出力。
  * `Convergence_` - `FixedPoint_`がそれを出力として生成した入力にどれだけ近いかを示す実数。
  * `TerminationCondition_' - 固定点加速が停止した理由。
  * `Iterations_' - 実施された反復の数。
  * `ConvergenceVector_` - 各反復での収束値。
  * `FailedEvaluation_` - 固定点反復が失敗した理由（失敗しなかった場合は欠落）。
  * `Inputs_` - 試みられたすべての入力。
  * `Outputs_` - 対応するすべての出力。
