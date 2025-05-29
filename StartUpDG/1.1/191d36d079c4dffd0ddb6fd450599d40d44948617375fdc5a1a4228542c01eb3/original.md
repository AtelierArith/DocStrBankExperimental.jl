```
function sparse_low_order_SBP_operators(rd; factor=1.01)
```

Constructs sparse low order SBP operators given a `RefElemData`.  Returns operators `Qrst..., E ≈ Vf * Pq` that satisfy a generalized  summation-by-parts (GSBP) property:

```
    `Q_i + Q_i^T = E' * B_i * E`
```

`factor` is a scaling which determines how close a node must be to  another node to be considered a neighbor.
