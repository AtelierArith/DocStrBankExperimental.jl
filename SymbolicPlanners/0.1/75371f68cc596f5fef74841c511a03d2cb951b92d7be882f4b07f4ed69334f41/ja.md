```
RealTimeDynamicPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(),
    n_rollouts::Int = 50,
    max_depth::Int = 50,
    rollout_noise::Float64 = 0.0,
    action_noise::Float64 = 0.0,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

リアルタイム動的プランナーは、初期状態から貪欲なロールアウトを行い、途中で遭遇した状態の価値推定を更新する非同期値反復の一形態であるリアルタイム動的プログラミング（略して`RTDP`）を使用します[1]。

`heuristic`が提供されると、否定されたヒューリスティック値が新たに遭遇した状態の初期価値推定として使用されます（最短経路問題における状態の価値は目標に到達するためのコストであるため）、これにより早期のロールアウトを導きます。

許容可能（すなわち楽観的）なヒューリスティックに対しては、十分な数のロールアウトの後に到達可能な状態空間内で真の価値関数への収束が保証されます。

遭遇した各状態の価値推定とアクションQ値を格納する[`TabularPolicy`](@ref)（`action_noise > 0`の場合は[`BoltzmannPolicy`](@ref)でラップされる）を返します。

[1] A. G. Barto, S. J. Bradtke, and S. P. Singh, "Learning to Act using Real-Time Dynamic Programming," Artificial Intelligence, vol. 72, no. 1, pp. 81–138, Jan. 1995, [https://doi.org/10.1016/0004-3702(94)00011-O](https://doi.org/10.1016/0004-3702(94)00011-O).

# 引数

  * `heuristic`: 価値関数を初期化するために使用される探索ヒューリスティック。
  * `n_rollouts`: 初期状態から実行するロールアウトの数。
  * `max_depth`: 各ロールアウトの最大深さ。
  * `rollout_noise`: シミュレートされたロールアウト中のボルツマンノイズの量。
  * `action_noise`: 返されるポリシーのボルツマンアクションノイズの量。
  * `verbose`: 検索中にデバッグ情報を印刷するためのフラグ。
  * `callback`: ロギングなどのためのコールバック関数。
