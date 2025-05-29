```
GradientScaleAdaptiveLoss(reweight_every;
                          weight_change_inertia = 0.9,
                          pde_loss_weights = 1.0,
                          bc_loss_weights = 1.0,
                          additional_loss_weights = 1.0)
```

損失関数の合計における成分を適応的に再重み付けする方法であり、BC*i 損失重みが max(|∇pde*loss|) / mean(|∇bc*i*loss|) の指数移動平均によってスケーリングされます。

## 位置引数

  * `reweight_every`: BC 損失関数を再重み付けする頻度で、イテレーションで測定されます。再重み付けは各成分損失関数の勾配を評価する必要があるため、やや高コストです。

## キーワード引数

  * `weight_change_inertia`: BC 重みの変化の指数移動平均の慣性を表す実数です。

## 参考文献

物理情報ニューラルネットワークにおける勾配病理の理解と緩和 Sifan Wang, Yujun Teng, Paris Perdikaris https://arxiv.org/abs/2001.04536v1

コードの参照: https://github.com/PredictiveIntelligenceLab/GradientPathologiesPINNs
