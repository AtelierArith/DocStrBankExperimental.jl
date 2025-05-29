```
parity_transform(call_price, opt::VanillaOption{T, E, Call, U}, spot, rate_curve)
```

Returns the call price unchanged. Useful for unified pricing APIs that accept both calls and puts.

# Arguments

  * `call_price`: Price of the call option.
  * `opt`: A `VanillaOption` with `Call()` payoff.
  * `spot`: Spot price.
  * `rate_curve`: Rate curve.

# Returns

  * The same `call_price`, unchanged.
