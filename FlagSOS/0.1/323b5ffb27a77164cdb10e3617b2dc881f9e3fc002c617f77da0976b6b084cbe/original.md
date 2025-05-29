```
PartiallyLabeledFlag{T} <: Flag where {T<:Flag}
```

A Flag `F` where the first `n` vertices are labeled. May have isolated vertices in the labeled part. Labeling such a Flag canonically cannot swap vertices in the labeled part, meaning the Flags 2-1-o and 1-2-o are different. If swaps there should be allowed, use a `ColoredFlag{T}` instead.
