```
longsymbol(s::Symbol)   → String
longsymbol(m::Monetary) → String
longsymbol(t::DataType) → String
```

Get a commonly-used currency symbol for a currency, with at least enough disambiguation to be non-ambiguous. This function may be called with either a symbol, a `Monetary` type, or a `Monetary` object.
