RolloutEstimator

もしこれがソルバーのestimate_valueフィールドに渡されると、ロールアウトが葉ノードでの値を推定するために使用されます。

フィールド:     solver::Union{Solver,Policy,Function}         これがSolverの場合、solve(solver, mdp)が呼び出されてロールアウトポリシーが見つかります         これがPolicyの場合、そのポリシーがロールアウトに使用されます         これがFunctionの場合、この関数を持つPOMDPToolbox.FunctionPolicyがロールアウトに使用されます     max_depth::Int         ロールアウトの深さ。これが-1の場合、ルートノードからの`MCTSSolver`の`depth`引数までロールアウトされます。     eps::Float64         小さな数; γᵗがこの値より小さくなる場合、ロールアウトは終了します。
