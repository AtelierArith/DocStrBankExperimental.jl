```
stochasticoscillator(ohlc, n = 14, fast_d = 3, slow_d = 3; h = :High, l = :Low, c = :Close)
```

Stochastic Oscillator

A.k.a *%K%D*, or *KD*

# Arguments

  * `n`: period of fast(raw) `%K`
  * `fast_d`: MA period of fast `%D`
  * `slow_d`: MA period of slow `%D`

# Formula

$$
\begin{align*}
  \text{fast %K} & = \frac{\text{Close}_t - \max(\text{High}_{t-n}, \dots, \text{High}_t)}
        {\max(\text{High}_{t-n}, \dots, \text{High}_t) - \min(\text{Low}_{t-n}, \dots, \text{Low}_t)}
        \times 100 \\
  \text{fast %D} & = \text{SMA}(\text{fast %K}) \\
  \text{slow %D} & = \text{SMA}(\text{fast %D})
\end{align*}
$$

# References

  * [Wikipedia](https://en.wikipedia.org/wiki/Stochastic_oscillator)
  * [FMLabs](http://www.fmlabs.com/reference/default.htm?url=StochasticOscillator.htm)
