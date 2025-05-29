```
type_upper_bound(::Type)::Type
```

Return a supertype of the provided type such that each value of one of the two types is also of the other type. The returned supertype may be simpler than its subtype, possibly leading to less compiler latency.
