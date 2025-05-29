```
yh = adaptive_filter(y, alg=MSPI; order=4, lr=0.1)
```

Filters `y` with an adaptive AR (only poles) filter with specified order. Returns `yh` which is the predicted output from an adaptive line enhancer (ALE). If your noise is wideband and signal narrowband, `yh` is your desired filtered signal. If the noise is narrowband and the signal is wideband, then `y-yh` is your desired filtered signal.

The first `order` samples of `yh` will be copies of `y`. The signals will thus have the same length.

#Arguments:

  * `alg`: Stochastic approximation algorithm or weight function. Examples: `OMAP, MSPI, OMAS, ADAM, ExponentialWeight, EqualWeight`
  * `y`: Input signal
  * `order`: Filter order
  * `lr`: Learning rate or weight depending on `alg`
