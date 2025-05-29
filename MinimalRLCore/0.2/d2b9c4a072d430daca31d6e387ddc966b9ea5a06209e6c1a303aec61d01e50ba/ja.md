```
Episode(env, agent, maxn, rng)
```

これはエピソードイテレータのコンポーネントを管理するための構造体です。envとagentへの参照のみを渡し、参照は別々に管理する必要があります。

# 引数

  * `env::AbstractEnvironment`: 環境（RLCoreインターフェースに従う）
  * `agent::AbstractAgent`: エージェント（RLCoreインターフェースに従う）
  * `maxn=0`: エピソードの最大ステップ数。
  * `rng=nothing`: エピソードのための乱数生成器（nothingまたはAbstractRNGのいずれかであることができます）
