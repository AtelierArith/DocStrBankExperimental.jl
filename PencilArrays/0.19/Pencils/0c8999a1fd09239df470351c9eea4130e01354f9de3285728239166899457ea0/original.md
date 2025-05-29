```
to_local(p::Pencil, global_inds, [order = LogicalOrder()])
```

Convert non-permuted (logical) global indices to local indices.

If `order = MemoryOrder()`, returned indices will be permuted using the permutation associated to the pencil configuration `p`.
