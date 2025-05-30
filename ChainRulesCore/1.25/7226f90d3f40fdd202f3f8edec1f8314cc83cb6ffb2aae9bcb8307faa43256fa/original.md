```
canonicalize(tangent::Tangent{P}) -> Tangent{P}
```

Return the canonical `Tangent` for the primal type `P`. The property names of the returned `Tangent` match the field names of the primal, and all fields of `P` not present in the input `tangent` are explictly set to `ZeroTangent()`.
