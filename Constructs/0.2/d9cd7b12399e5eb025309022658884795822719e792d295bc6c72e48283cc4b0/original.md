```
Adapter(T|subcon, encode) -> SymmetricAdapter{T}
SymmetricAdapter(T|subcon, encode) -> SymmetricAdapter{T}
```

Create a symmetric adapter based on the `encode` function.

# Arguments

  * `subcon::Construct{T}`: the underlying construct.
  * `encode`: the encoding function. the function should have signature like `(::T; contextkw...)->T` and satisfies involution (`encode(encode(x)) == x`).
