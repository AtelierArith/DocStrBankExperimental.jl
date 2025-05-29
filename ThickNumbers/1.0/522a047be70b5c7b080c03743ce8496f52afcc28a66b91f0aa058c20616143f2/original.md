```
is_strict_subset_tn(a::ThickNumber, b::ThickNumber)
⪽(a::ThickNumber, b::ThickNumber)
```

Returns `true` if `a` is a strict subset of `b`, `false` otherwise. `a` is a strict subset if `a` is a subset of `b` not equal to `b`.

See documentation for why this is not just `⊂`.
