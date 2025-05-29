```
StaticBitVector{N, [U]}(f)
StaticBitVector{N, [U]}([bit])
```

A statically sized analogue of `BitVector` with `Unsigned` chunks of type `U`, which can be constructed using either a function `f(n)` or a constant `bit`. By default, `U` is set to `UInt8` and `bit` is set to `false`.

This iterator can only store `Bool`s, so its `output_type_for_promotion` is a `ConditionalOutputType`. Efficient implementations are provided for all unrolled functions, though the methods for `unrolled_map` and `unrolled_accumulate` only apply when the first item in the output is a `Bool`.
