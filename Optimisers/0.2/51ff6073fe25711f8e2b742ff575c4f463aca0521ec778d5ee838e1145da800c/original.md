```
AdaDelta(ρ = 9f-1, ϵ = eps(typeof(ρ)))
```

[AdaDelta](https://arxiv.org/abs/1212.5701) is a version of AdaGrad adapting its learning rate based on a window of past gradient updates. Parameters don't need tuning.

# Parameters

  * Rho (`ρ`): Factor by which the gradient is decayed at each time step.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
