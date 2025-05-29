```
iso4217num(s::Symbol)   → Int
iso4217num(m::Monetary) → Int
iso4217num(t::DataType) → Int
```

Get the ISO 4217 numeric code for a currency. For custom currencies, a value of `0` will be returned. This function may be called with either a symbol, a `Monetary` type, or a `Monetary` object. Note that most applications should zero-pad this code to three digits.
