```
VanillaOption{TS,TE,E,C,U} <: AbstractPayoff
```

A vanilla option with specified exercise style, call/put type, and underlying type.

# Fields

  * `strike`: The strike price of the option.
  * `expiry`: The expiry (maturity) time in internal tick units.
  * `exercise_style`: Instance of `European` or `American`.
  * `call_put`: Instance of `Call` or `Put`.
  * `underlying`: Either `Spot` or `Forward`.
