MCTSソルバータイプ

# フィールド

  * `n_iterations::Int64=100` 各action()呼び出し中の反復回数。
  * `max_time::Float64=Inf` シミュレーションを反復するのに費やす最大CPU時間（秒単位）。
  * `depth::Int64=10`: 最大ツリー探索深度。ロールアウト深度は`estimate_value`フィールドを介して制御されます。
  * `exploration_constant::Float64=1.0`: ソルバーがどれだけ探索すべきかを指定します。UCB方程式では、Q + c*sqrt(log(t/N))のcが探索定数です。
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: 擬似乱数生成器
  * `estimate_value::Any=RolloutEstimator(RandomSolver(rng))`: 葉ノードでの値を推定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, remaining_depth)`が呼び出されて値が推定されます（remaining_depthは無視できます）。
      * これがオブジェクト`o`の場合、`estimate_value(o, mdp, s, remaining_depth)`が呼び出されます。
      * これが数値の場合、その数値に値が設定されます。
  * `init_Q::Any=0.0`: 新しいノードでの初期Q(s,a)値を設定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, a)`が呼び出されて値が設定されます。
      * これがオブジェクト`o`の場合、`init_Q(o, mdp, s, a)`が呼び出されます。
      * これが数値の場合、Qはその数値に設定されます。
  * `init_N::Any=0`: 新しいノードでの初期N(s,a)値を設定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, a)`が呼び出されて値が設定されます。
      * これがオブジェクト`o`の場合、`init_N(o, mdp, s, a)`が呼び出されます。
      * これが数値の場合、Nはその数値に設定されます。
  * `reuse_tree::Bool=false`: これがtrueの場合、次の計画を計算するためにツリー情報が再利用されます。もちろん、clear_tree!を呼び出してこれを上書きすることもできます。
  * `enable_tree_vis::Bool=false`: これがtrueの場合、ツリーの視覚化に必要な追加情報が記録されます。falseの場合、ツリーは視覚化できません。
  * `timer::Function=()->1e-9*time_ns()`: 時間計測方法。`timer() - start_time ≥ max_time`のときに探索反復が終了します。
