```
shortsymbol(s::Symbol)   → String
shortsymbol(m::Monetary) → String
shortsymbol(t::DataType) → String
```

Get a short, possibly ambiguous, commonly-used symbol for a currency. This function may be called with either a symbol, a `Monetary` type, or a `Monetary` object.
