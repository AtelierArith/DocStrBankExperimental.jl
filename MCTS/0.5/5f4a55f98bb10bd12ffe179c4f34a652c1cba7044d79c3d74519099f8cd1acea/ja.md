MCTSソルバーとDPW

# フィールド

  * `depth::Int64=10`: 最大ツリー探索深度。ロールアウト深度は`estimate_value`フィールドによって制御されます。
  * `exploration_constant::Float64=1.0`: ソルバーがどれだけ探索すべきかを指定します。UCB方程式では、Q + c*sqrt(log(t/N))のcが探索定数です。
  * `n_iterations::Int64=100`: 各`action()`呼び出し中の反復回数。
  * `max_time::Float64`: シミュレーションを反復するのに費やす最大CPU時間（秒）。
  * ダブルプログレッシブワイディングパラメータ。これらの定数はダブルプログレッシブワイディングを制御します。子の数がkN^alpha以下の場合、新しい状態またはアクションが追加されます。

      * `k_action::Float64=10`
      * `alpha_action::Float64=0.5`
      * `k_state::Float64=10`
      * `alpha_state::Float64=0.5`
  * `keep_tree::Bool=false`: trueの場合、次のタイムステップで再利用するためにプランナーにツリーを保存します（将来使用されるたびに）。これには、必要な状態辞書を維持するための計算コストがあります。
  * `enable_action_pw::Bool=true`: trueの場合、アクション空間でのプログレッシブワイディングを有効にします。falseの場合は、全アクション空間を使用します。
  * `enable_state_pw::Bool=true`: trueの場合、状態空間でのプログレッシブワイディングを有効にします。falseの場合は、単一の次の状態のみを使用します（決定論的問題の場合）。
  * `check_repeat_state::Bool=true`, `check_repeat_action::Bool=true`: ツリーを構築する際に、状態またはアクションが以前に見られたかどうかを確認します（これには、必要な辞書を維持するための計算コストがあります）。
  * `tree_in_info::Bool=false`: trueの場合、`action_info`が呼び出されたときに情報辞書にツリーを返します。デフォルトではfalseで、履歴が保存されている場合は多くのメモリを使用する可能性があります。
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: 擬似乱数生成器
  * `estimate_value::Any=RolloutEstimator(RandomSolver(rng))`: （ロールアウトポリシー）葉ノードでの値を推定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, depth)`が呼び出されて値が推定されます（深度は無視できます）。
      * これがオブジェクト`o`の場合、`estimate_value(o, mdp, s, depth)`が呼び出されます。
      * これが数値の場合、その数値に値が設定されます。
  * `init_Q::Any=0.0`: 新しいノードでの初期Q(s,a)値を設定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, a)`が呼び出されて値が設定されます。
      * これがオブジェクト`o`の場合、`init_Q(o, mdp, s, a)`が呼び出されます。
      * これが数値の場合、Qは常にその数値に設定されます。
  * `init_N::Any=0`: 新しいノードでの初期N(s,a)値を設定するために使用される関数、オブジェクト、または数値。

      * これが関数`f`の場合、`f(mdp, s, a)`が呼び出されて値が設定されます。
      * これがオブジェクト`o`の場合、`init_N(o, mdp, s, a)`が呼び出されます。
      * これが数値の場合、Nは常にその数値に設定されます。
  * `next_action::Any=RandomActionGenerator(rng)`: プログレッシブワイディングのために考慮される次のアクションを選択するために使用される関数またはオブジェクト。次のアクションはMDP、状態`s`、および現在の`DPWStateNode`、`snode`に基づいて決定されます。

      * これが関数`f`の場合、`f(mdp, s, snode)`が呼び出されて値が設定されます。
      * これがオブジェクト`o`の場合、`next_action(o, mdp, s, snode)`が呼び出されます。
  * `default_action::Any=ExceptionRethrow()`: POMCPが例外`ex`で失敗した場合にアクションを決定するために使用される関数、アクション、またはポリシー。

      * これが関数`f`の場合、`f(pomdp, belief, ex)`が呼び出されます。
      * これがポリシー`p`の場合、`action(p, belief)`が呼び出されます。
      * これがオブジェクト`a`の場合、`default_action(a, pomdp, belief, ex)`が呼び出され、このメソッドが実装されていない場合は、`a`が直接返されます。
  * `reset_callback::Function=(mdp, s)->false`: MDPを指定された状態`s`にリセット/再初期化するために使用される関数。シミュレーターの状態がMDPの状態と真に分離されていない場合に便利です。`f(mdp, s)`が呼び出されます。デフォルトでは、これはコンパイラによって最適化されます。
  * `show_progress::Bool=false`: シミュレーション中に進行状況バーを表示します。
  * `timer::Function=()->1e-9*time_ns()`: 時間計測メソッド。`timer() - start_time ≥ max_time`のときに探索反復が終了します。
