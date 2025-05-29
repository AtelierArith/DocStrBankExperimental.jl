```
MultiArmBanditsEnv(;true_reward=0., k = 10,rng=Random.default_rng())
```

`true_reward`は期待される報酬です。`k`はアームの数です。詳細な説明については、[multi-armed bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit)を参照してください。

これは**一回限り**のゲームです。環境はアクションを取った後すぐに終了します。ここでは、最小限のインターフェースのみが定義されたカスタマイズされた環境を書く方法を示すために使用します。
