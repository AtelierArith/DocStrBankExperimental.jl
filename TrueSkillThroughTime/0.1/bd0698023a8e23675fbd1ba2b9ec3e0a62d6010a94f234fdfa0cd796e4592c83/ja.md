`Gaussian`クラスは、エージェントのスキルに関する事前の信念（および内部計算）を定義するために使用されます。

パラメータを順番に渡すか、名前を指定することでオブジェクトを作成できます。

```
Gaussian(mu::Float64=MU, sigma::Float64=SIGMA)
Gaussian(;mu::Float64=MU, sigma::Float64=SIGMA)
```

  * `mu`はガウス分布の平均です
  * `sigma`はガウス分布の標準偏差です
