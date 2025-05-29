```
(payoff::VanillaOption)(spot)
```

Computes the intrinsic payoff of a vanilla option for a given spot price or array of spot prices.

# Arguments

  * `payoff`: A `VanillaOption` instance.
  * `spot`: A single spot price (`Real`) or an array of spot prices.

# Returns

  * The intrinsic value(s), i.e. `max(cp * (S - K), 0)`, where `cp` is +1 for a call and -1 for a put.
