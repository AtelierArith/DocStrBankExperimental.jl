```
abstract type Action
```

モンテカルロのアクション/ムーブを表す抽象型で、システムに対して実行可能です。

具体的なサブタイプは以下を実装する必要があります：

  * `sample_action!(action, policy, parameters, system, rng)`: ポリシーから新しいアクションをサンプリングします
  * `perform_action!(system, action)`: アクションを適用してシステムの状態を変更します
  * `invert_action!(action, system)`: アクションを反転/逆転させます
  * `log_proposal_density(action, policy, parameters, system)`: このアクションを提案する確率密度をログします

オプションのメソッド：

  * `revert_action!(system, action)`: キャッシュされた値を再利用できる最適化されたバージョンのperform_action!です
