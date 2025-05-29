```
Bits(input::Integer)
Bits{T}(input::Integer)
Bits{T}(input)
```

Construct a `Bits` from the bits in `input`, passed either as a `Integer` or from an array, or any other generic iterable. It is basically a view into the bits of `input`, which can then be manipulated using vector-like syntax.
