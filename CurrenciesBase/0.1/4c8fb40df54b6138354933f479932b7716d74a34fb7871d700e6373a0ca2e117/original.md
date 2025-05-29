```
iso4217alpha(s::Symbol)   → String
iso4217alpha(m::Monetary) → String
iso4217alpha(t::DataType) → String
```

Get the ISO 4217 alphabetic code for a currency. For custom currencies, a lowercase string will be returned, and this should not be interpreted as an ISO 4217 code. Otherwise, a three-letter uppercase string will be returned. This function may be called with either a symbol, a `Monetary` type, or a `Monetary` object.
