```
MiniMaxAdaptiveLoss(reweight_every;
                    pde_max_optimiser = OptimizationOptimisers.Adam(1e-4),
                    bc_max_optimiser = OptimizationOptimisers.Adam(0.5),
                    pde_loss_weights = 1, bc_loss_weights = 1,
                    additional_loss_weights = 1)
```

A way of adaptively reweighting the components of the loss function in the total sum such that the loss weights are maximized by an internal optimizer, which leads to a behavior where loss functions that have not been satisfied get a greater weight.

## Positional Arguments

  * `reweight_every`: how often to reweight the PDE and BC loss functions, measured in iterations.  Reweighting is cheap since it re-uses the value of loss functions generated during the main optimization loop.

## Keyword Arguments

  * `pde_max_optimiser`: a OptimizationOptimisers optimiser that is used internally to maximize the weights of the PDE loss functions.
  * `bc_max_optimiser`: a OptimizationOptimisers optimiser that is used internally to maximize the weights of the BC loss functions.

## References

Self-Adaptive Physics-Informed Neural Networks using a Soft Attention Mechanism Levi McClenny, Ulisses Braga-Neto https://arxiv.org/abs/2009.04544
