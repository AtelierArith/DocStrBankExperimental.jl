```
B = block_diag(As::LinearMapAX... ; tryop::Bool)
```

Make block diagonal `LinearMapAX` object from blocks.

Return a `LinearMapAM` unless `tryop` and all blocks have same `idim` and `odim`.

Default for `tryop` is `true` if all blocks are type `LinearMapAO`.
