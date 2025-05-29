```
GradientScaleAdaptiveLoss(reweight_every;
                          weight_change_inertia = 0.9,
                          pde_loss_weights = 1.0,
                          bc_loss_weights = 1.0,
                          additional_loss_weights = 1.0)
```

A way of adaptively reweighting the components of the loss function in the total sum such that BC*i loss weights are scaled by the exponential moving average of max(|∇pde*loss|) / mean(|∇bc*i*loss|)).

## Positional Arguments

  * `reweight_every`: how often to reweight the BC loss functions, measured in iterations. Reweighting is somewhat expensive since it involves evaluating the gradient of each component loss function,

## Keyword Arguments

  * `weight_change_inertia`: a real number that represents the inertia of the exponential moving average of the BC weight changes,

## References

Understanding and mitigating gradient pathologies in physics-informed neural networks Sifan Wang, Yujun Teng, Paris Perdikaris https://arxiv.org/abs/2001.04536v1

With code reference: https://github.com/PredictiveIntelligenceLab/GradientPathologiesPINNs
