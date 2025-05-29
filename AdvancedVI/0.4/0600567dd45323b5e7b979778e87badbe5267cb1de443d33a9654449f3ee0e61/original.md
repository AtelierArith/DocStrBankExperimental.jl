```
COCOB(alpha)
```

Continuous Coin Betting (COCOB[^OT2017]) optimizer. We use the "COCOB-Backprop" variant, which is closer to the Adam optimizer. It's only parameter is the maximum change per parameter α, which shouldn't need much tuning.

# Parameters

  * `alpha`: Scaling parameter. (default value: `100`)

[^OT2017]: Orabona, F., & Tommasi, T. (2017). Training deep networks without learning rates through coin betting. Advances in Neural Information Processing Systems, 30.
