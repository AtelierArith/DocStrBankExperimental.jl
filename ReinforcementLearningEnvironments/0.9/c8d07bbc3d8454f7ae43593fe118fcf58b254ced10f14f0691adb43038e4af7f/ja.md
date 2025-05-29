```
discrete2standard_discrete(env)
```

離散アクション空間を持つ`env`を標準形式に変換します：

  * アクション空間は`Base.OneTo`型です。
  * `env`が`FULL_ACTION_SET`の場合、`legal_action_space(env)`内の各アクションもアクション空間内の`Int`です。

標準形式は、いくつかのアルゴリズム（Q学習など）にとって便利です。
