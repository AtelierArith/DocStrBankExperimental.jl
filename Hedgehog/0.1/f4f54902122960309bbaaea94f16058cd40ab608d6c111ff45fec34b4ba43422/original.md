```
VanillaOption(strike, expiry_date, exercise_style, call_put, underlying)
```

Constructs a `VanillaOption` using a calendar `expiry_date` (e.g. `Date`, `DateTime`, etc.), which is converted internally to tick units via `to_ticks`.

# Arguments

  * `strike`: Strike price of the option.
  * `expiry_date`: Maturity as a date/time object (converted to ticks).
  * `exercise_style`: `European()` or `American()`.
  * `call_put`: `Call()` or `Put()`.
  * `underlying`: `Spot()` or `Forward()`.

# Returns

  * A fully constructed `VanillaOption` instance.
