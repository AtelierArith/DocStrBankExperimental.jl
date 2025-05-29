```
binderloss(a::ClustLabelVector, b::ClustLabelVector;
normalised = true) -> Float64
```

Computes the Binder loss between two clusterings. If `normalised = true` then the result is equal to one minus the rand index between `a` and `b`.
