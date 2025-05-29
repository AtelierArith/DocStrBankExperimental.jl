`Player`クラスはエージェントの特徴を定義するために使用されます。パラメータを順番に指定するか、名前を挙げることでオブジェクトを作成できます。

```
Player(prior::Gaussian=Gaussian(MU,SIGMA), beta::Float64=BETA, gamma::Float64=GAMMA)
Player(;prior::Gaussian=Gaussian(MU,SIGMA), beta::Float64=BETA, gamma::Float64=GAMMA)
```

  * `prior`はスキル仮説の事前信念分布です
  * `beta`はエージェントのパフォーマンスの標準偏差です
  * `gamma`は時間が経過するにつれて推定値に加えられる不確実性（標準偏差）です
