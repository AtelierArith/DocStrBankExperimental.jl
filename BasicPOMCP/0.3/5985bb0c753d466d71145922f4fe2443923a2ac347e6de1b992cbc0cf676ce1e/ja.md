```
POMCPSolver(#=キーワード引数=#)
```

部分的に観測可能なモンテカルロ計画ソルバー。

## キーワード引数

  * `max_depth::Int`   ロールアウトとツリーの拡張は、この深さに達したときに停止します。   デフォルト: `20`
  * `c::Float64`   UCB探索定数 - ソルバーがどれだけ探索すべきかを指定します。   デフォルト: `1.0`
  * `tree_queries::Int`   各 action() 呼び出し中の反復回数。   デフォルト: `1000`
  * `max_time::Float64`   各 action() 呼び出し中の計画の最大時間。   デフォルト: `Inf`
  * `tree_in_info::Bool`   `true` の場合、action_info が呼び出されたときに情報辞書にツリーを返します。   デフォルト: `false`
  * `estimate_value::Any`   葉ノードでの値を推定するために使用される関数、オブジェクト、または数値。   デフォルト: `RolloutEstimator(RandomSolver(rng))`

      * これが関数 `f` の場合、`f(pomdp, s, h::BeliefNode, steps)` が値を推定するために呼び出されます。
      * これがオブジェクト `o` の場合、`estimate_value(o, pomdp, s, h::BeliefNode, steps)` が呼び出されます。
      * これが数値の場合、その数値に値が設定されます。

    注: 多くの場合、値を推定する最も簡単な方法は、状態の関数であるポリシーを使用して完全に観測可能なMDPでロールアウトを行うことです。これを行うには、`FORollout(policy)` を使用します。
  * `default_action::Any`   POMCPが例外 `ex` で失敗した場合にアクションを決定するために使用される関数、アクション、またはポリシー。   デフォルト: `ExceptionRethrow()`

      * これが関数 `f` の場合、`f(pomdp, belief, ex)` が呼び出されます。
      * これがポリシー `p` の場合、`action(p, belief)` が呼び出されます。
      * これがオブジェクト `a` の場合、`default_action(a, pomdp, belief, ex)` が呼び出され、もしこのメソッドが実装されていない場合、`a` が直接返されます。
  * `time::Function`   秒単位で時間を取得するために呼び出す関数。これは最大時間に達したかどうかを確認するために使用されます。   デフォルト: `() -> time_ns()*1e-9`
  * `rng::AbstractRNG`   擬似乱数生成器。   デフォルト: `Random.GLOBAL_RNG`
