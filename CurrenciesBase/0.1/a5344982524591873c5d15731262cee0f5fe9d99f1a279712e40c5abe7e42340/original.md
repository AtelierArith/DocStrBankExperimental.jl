```
currency(m::Monetary) → Symbol
```

Return a symbol corresponding to the ISO 4217 currency code of the currency that the given monetary amount is representing. For example, `currency(80USD)` will return `:USD`. If the given monetary value is of a non-ISO 4217 currency, then the returned symbol should contain only lowercase letters.

Prefer `iso4217alpha` to this function if a string is desired.
