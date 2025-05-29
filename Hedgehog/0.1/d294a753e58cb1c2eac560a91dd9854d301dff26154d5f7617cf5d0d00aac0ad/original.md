```
parity_transform(call_price, opt::VanillaOption{T, E, Put, U}, spot, rate_curve)
```

Applies put-call parity to recover the put price from a known call price.

# Arguments

  * `call_price`: Price of the call option.
  * `opt`: A `VanillaOption` with `Put()` payoff.
  * `spot`: Spot price.
  * `rate_curve`: Rate curve.

# Returns

  * The corresponding put price using the formula: `put = call - S + K * exp(-rT)` where `T` is extracted from `opt.expiry`.
