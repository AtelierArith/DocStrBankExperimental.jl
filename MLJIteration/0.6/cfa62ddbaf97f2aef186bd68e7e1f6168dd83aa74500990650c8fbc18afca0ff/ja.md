```
CycleLearningRate(stepsize=4, lower=0.001, upper=0.05, learning_rate_parameter=:(optimiser.η))
```

イテレーション制御、すなわち `CycleLearningRate(learning_rate_parameter=:learning_rate)`。

指定された `learning_rate_parameter`（MLJFluxモデルに適したフィールドにデフォルト設定）を、指定された `upper` および `lower` 学習率の境界を使用して、三角形の周期的学習率ポリシーの次の値に変化させます。詳細は [L. N. Smith (2019)](https://ieeexplore.ieee.org/document/7926641): "Cyclical Learning Rates for Training Neural Networks," 2017 IEEE Winter Conference on Applications of Computer Vision (WACV), Santa Rosa, CA, USA, pp. 464-472 を参照してください。

ここで `stepsize` は、基礎となるモデルのイテレーションで測定された変異サイクルの半分の周期です。たとえば、`stepsize=4` は、MLJFluxモデルにおいて学習率が8エポックごとに1サイクルの変異を受けることを意味します。

**注意。** "1イテレーション" は MLJFluxモデルにおける "1エポック" と同じであるため、これは学習率の更新がエポックごとに最大1回適用できることを意味し、引用された論文のようにエポック全体にわたって "継続的に" 適用されるわけではありません。
