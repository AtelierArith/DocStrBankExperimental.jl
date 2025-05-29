```
lop3(a, b, c, lut)
```

Arbitrary logical operation on 3 inputs.

Call the [PTX `prmt` instruction](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#data-movement-and-conversion-instructions-prmt). This computes a bitwise logical operation on the inputs `a`, `b`, and `c`.

See [`make_lop3_lut`](@ref) for creating the look-up table `lut`.
