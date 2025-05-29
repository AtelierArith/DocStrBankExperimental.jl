```
majorunit(s::Symbol)   → Monetary{s}
majorunit(m::Monetary) → typeof(m)
majorunit(t::DataType) → t
```

Get the major unit of the currency. This function may be called with either a symbol, a `Monetary` type, or a `Monetary` object.
