```
QBasedPolicy(;learner, explorer)
```

学習者と探索者をラップします。学習者は、現在の状態における環境の各合法的なアクションのQ値を予測する構造体です。通常はテーブルまたはニューラルネットワークです。QBasedPolicyは、`RLBase.plan!`を使用してアクションを照会でき、探索者はアクションの選択に影響を与えます。
