```
sample_action!(action::Action, policy::Policy, parameters, system::AriannaSystem, rng)
```

ポリシーから新しいアクションをサンプリングします。

# 引数

  * `action`: サンプリングされるアクション
  * `policy`: サンプリング元のポリシー
  * `parameters`: ポリシーのパラメータ
  * `system`: アクションが適用されるシステム
  * `rng`: 擬似乱数生成器
