```julia
mutable struct Optimizer{Q, S, T} <: MathOptInterface.AbstractOptimizer
```

EAGOによって最適化ルーチン中に問題を解決するために使用される最高レベルの最適化オブジェクト。追加のオプションと一時的なストレージは、`_global_optimizer::GlobalOptimizer{Q,S,T}`フィールドにあります。解決全体を通じて一定であると予想されるパラメータは、`_parameters::EAGOParameters`フィールドに格納されます。`EAGOParameters`フィールドに含まれないユーザー向けのキーワードには以下が含まれます：

  * `relaxed_optimizer::MOI.AbstractOptimizer`: 緩和された部分問題を解決するために使用される最適化器のインスタンス（デフォルト = `Cbc.Optimizer()`）。`subsolver_block::SubSolvers{Q,S,T}`にあります。
  * `upper_optimizer::MOI.AbstractOptimizer`: 上限問題を解決するために使用される最適化器（デフォルト = `Ipopt.Optimizer()`）。`subsolver_block::SubSolvers{Q,S,T}`にあります。
  * `ext::ExtensionType`: 新しいカスタムサブルーチンを定義するために使用される`EAGO.ExtensionType`のサブタイプのインスタンスを保持します（デフォルト = `DefaultExt()`）。`subsolver_block::SubSolvers{Q,S,T}`にあります。
  * `enable_optimize_hook::Bool`: ユーザー定義の`optimize_hook!`関数を呼び出すべきであることを指定し、標準のEAGO最適化ルーチンを使用しないようにします。`Optimizer`および`_global_optimizer::GlobalOptimizer{Q,S,T}`にあります。
  * `obbt_variable_values::Vector{Bool}`: OBBTを実行する変数（デフォルト：非線形式のすべての変数）。`_global_optimizer::GlobalOptimizer{Q,S,T}`にあります。

拡張ヘルプで利用可能なすべての`Optimizer`フィールドの説明。

# 拡張ヘルプ

  * `subsolver_block::EAGO.SubSolvers{Q, S, T} where {Q, S, T}`: 緩和および上限最適化器の定義と、ユーザー定義の拡張タイプを保持します
  * `enable_optimize_hook::Bool`: optimize_hook!関数を呼び出すべきであることを指定し、標準ルーチンに問題を投げないようにします
  * `ext::Union{Nothing, T} where T`: （非推奨、代わりに`subsolver_block`を使用）カスタム拡張タイプのストレージ
  * `_auxiliary_variable_info::Union{Nothing, EAGO._AuxVarData}`: すべての補助変数に関する情報
  * `_global_optimizer::EAGO.GlobalOptimizer{Q, S, T} where {Q, S, T}`: 最適化問題を解決するための追加のオプションと一時的なストレージ
  * `_input_problem::EAGO.InputProblem`: EAGOモデルに追加された式と制約（緩和には直接使用されません）
  * `_working_problem::EAGO.ParsedProblem`: EAGOが緩和された問題を定式化するために使用する式と問題の説明
  * `_parameters::EAGO.EAGOParameters`: グローバル解決中に変更されないパラメータ
  * `_optimizer_attributes_set::Vector{MathOptInterface.AbstractOptimizerAttribute}`: 最適化器属性のセット
  * `_termination_status_code::MathOptInterface.TerminationStatusCode`: MathOptInterface準拠の完了ステータスコード
  * `_result_status_code::MathOptInterface.ResultStatusCode`: 結果の実現可能性ステータスを示す値
  * `_run_time::Float64`: 最適化実行時間
  * `_objective_value::Float64`: プライマル解の目的値
  * `_objective_bound::Float64`: 最適目的値に対する最良の既知の境界
  * `_relative_gap::Float64`: 上限と下限の間のギャップ、大きな絶対値を持つ境界に対して相対的
  * `_iteration_count::Int64`: 分岐限定アルゴリズムが完了した反復の数
  * `_node_count::Int64`: スタック内のノードの数
