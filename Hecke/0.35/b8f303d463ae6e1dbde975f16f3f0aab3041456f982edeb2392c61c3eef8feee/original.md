```
completion(K::AbsSimpleNumField, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, precision::Int)
                                                -> LocalField, CompletionMap
```

The completion of $K$ wrt to the topology induced by the valuation at $P$, presented as a Eisenstein extension of an unramified p-adic field.

The map giving the embedding of $K$ into the completion, admits a pointwise preimage to obtain a lift. Note, that the map is not well defined by this data: $K$ will have $\deg P$ many embeddings.

The map is guaranteed to yield a relative precision of at least `preciscion`.
