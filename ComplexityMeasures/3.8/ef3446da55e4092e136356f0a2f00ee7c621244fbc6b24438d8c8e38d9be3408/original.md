```
encode(c::Encoding, χ) -> i::Int
```

Encode an element `χ ∈ x` of input data `x` (those given to e.g., [`counts`](@ref)) into the **positive integers** using encoding `c`. The special value of `i = -1` is used as a return value for inappropriate elements `χ` that cannot be encoded according to `c`.
