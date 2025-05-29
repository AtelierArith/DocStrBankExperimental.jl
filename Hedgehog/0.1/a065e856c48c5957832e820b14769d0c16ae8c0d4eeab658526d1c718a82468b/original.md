The Cox-Ross-Rubinstein binomial tree pricing method.

This struct represents the Cox-Ross-Rubinstein (CRR) binomial pricing model for option pricing.

# Fields

  * `steps`: The number of time steps in the binomial tree.

# Notes

  * This implementation supports options written on either the **forward price** or the **spot price**.
  * When pricing an option on the forward price, discounting is already embedded in the forward.
  * When pricing an option on the spot price, discounting must be explicitly applied at each step.
  * The up probability is defined as:

```
p = 1 / (1 + u)
```

where:

  * `u = exp(σ√ΔT)` is the up-move factor,
  * `ΔT` is the time step duration in years.
