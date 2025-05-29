```
ClosedFormEntropyZeroGradient()
```

Use closed-form expression of entropy but detach it from the AD graph. This is expected to be used only with `ProximalLocationScaleEntropy`.

# Requirements

  * The variational approximation implements `entropy`.
