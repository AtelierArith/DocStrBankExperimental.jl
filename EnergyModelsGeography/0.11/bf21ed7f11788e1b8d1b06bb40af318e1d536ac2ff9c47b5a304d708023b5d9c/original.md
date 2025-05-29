```
exchange_limit(a::LimitedExchangeArea)
exchange_limit(a::LimitedExchangeArea, p::Resource)
exchange_limit(a::LimitedExchangeArea, p::Resource, t)
```

Returns the limits of the exchange resources in area `a` as dictionary, the value of resource `p` as `TimeProfile`, or the value of resource p in operational period `t`.

If the resource `p` is not included, the function returns either a `FixedProfile(0)` or a value of 0.
