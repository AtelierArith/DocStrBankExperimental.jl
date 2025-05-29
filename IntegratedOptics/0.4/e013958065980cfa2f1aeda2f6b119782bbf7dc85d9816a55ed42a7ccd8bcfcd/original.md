```
ADADelta(ρ = 0.9)
```

[ADADelta](https://arxiv.org/abs/1212.5701) is a version of ADAGrad adapting its learning rate based on a window of past gradient updates. Parameters don't need tuning.

# Parameters

  * Rho (`ρ`): Factor by which the gradient is decayed at each time step.

# Examples

```julia
opt = ADADelta()
opt = ADADelta(0.89)
```
