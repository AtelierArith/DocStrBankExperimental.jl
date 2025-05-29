```
BasicDQNLearner(;kwargs...)
```

論文を参照してください: [Playing Atari with Deep Reinforcement Learning](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)

これはDQNの非常に基本的な実装です。従来のQ学習と比較して、最適化ステップでは現在の遷移の代わりに経験バッファからサンプリングされた遷移のバッチを使用するという唯一の違いがあります。また、Q値を推定するためにニューラルネットワークが使用されます。この実装から始めて、すべてがどのように整理されているか、そして自分自身のカスタマイズされたアルゴリズムを書く方法を理解することができます。

# キーワード引数

  * `approximator`::[`Approximator`](@ref): 状態のQ値を取得するために使用されます。
  * `loss_func=huber_loss`: 使用する損失関数。
  * `γ::Float32=0.99f0`: 割引率。
