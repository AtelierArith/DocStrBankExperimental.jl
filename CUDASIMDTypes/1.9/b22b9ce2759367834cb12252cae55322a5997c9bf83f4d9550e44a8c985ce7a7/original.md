```
prmt(a, b, op)
```

Permute bytes bytes from a pair of inputs.

Call the [PTX `prmt` instruction](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#data-movement-and-conversion-instructions-prmt). This picks four arbitrary bytes from the input values `a` and `b`.
