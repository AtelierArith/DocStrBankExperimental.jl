```
MiniMaxAdaptiveLoss(reweight_every;
                    pde_max_optimiser = OptimizationOptimisers.Adam(1e-4),
                    bc_max_optimiser = OptimizationOptimisers.Adam(0.5),
                    pde_loss_weights = 1, bc_loss_weights = 1,
                    additional_loss_weights = 1)
```

損失関数の合計におけるコンポーネントを適応的に再重み付けする方法であり、内部オプティマイザによって損失重みが最大化されるため、満たされていない損失関数にはより大きな重みが与えられます。

## 位置引数

  * `reweight_every`: PDEおよびBC損失関数を再重み付けする頻度（イテレーション単位）。再重み付けは、メインの最適化ループ中に生成された損失関数の値を再利用するため、コストが低いです。

## キーワード引数

  * `pde_max_optimiser`: PDE損失関数の重みを最大化するために内部で使用されるOptimizationOptimisersオプティマイザ。
  * `bc_max_optimiser`: BC損失関数の重みを最大化するために内部で使用されるOptimizationOptimisersオプティマイザ。

## 参考文献

自己適応型物理インフォームドニューラルネットワークにおけるソフトアテンションメカニズム Levi McClenny, Ulisses Braga-Neto https://arxiv.org/abs/2009.04544
