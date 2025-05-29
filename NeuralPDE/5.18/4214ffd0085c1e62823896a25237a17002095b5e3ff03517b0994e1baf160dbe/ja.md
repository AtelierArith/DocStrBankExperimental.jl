```
QuasiRandomTraining(points; bcs_points = points,
                            sampling_alg = LatinHypercubeSample(), resampling = true,
                            minibatch = 0)
```

高次元空間における純粋なランダムシーケンスに対して収束を加速する低差異シーケンスのための準モンテカルロサンプリングを使用するトレーニング戦略です。

## 位置引数

  * `points`: サンプル内の準ランダムポイントの数

## キーワード引数

  * `bcs_points`: 境界条件のためのサンプル内の準ランダムポイントの数（デフォルトでは`points`と等しい）、
  * `sampling_alg`: 準モンテカルロサンプリングアルゴリズム、
  * `resampling`: falseの場合 - トレーニング前にフルトレーニングセットが事前に生成され、各イテレーションでバッチからランダムに1つのサブセットが選択されます。trueの場合 - トレーニングセットは事前に生成されず、各イテレーションでランタイムに直接1セットの準ランダムポイントが生成されます。この場合、`minibatch`は効果がありません。
  * `minibatch`: サブセットの数、`!resampling`の場合。

詳細については、[QuasiMonteCarlo.jl](https://docs.sciml.ai/QuasiMonteCarlo/stable/)を参照してください。
