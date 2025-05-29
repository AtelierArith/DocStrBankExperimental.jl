```
*(As::ITensor...; sequence = default_sequence(), kwargs...)
*(As::Vector{<: ITensor}; sequence = default_sequence(), kwargs...)
contract(As::ITensor...; sequence = default_sequence(), kwargs...)
```

Contract the set of ITensors according to the contraction sequence.

The default sequence is "automatic" if `ITensors.using_contraction_sequence_optimization()` is true, otherwise it is "left_associative" (the ITensors are contracted from left to right).

You can change the default with `ITensors.enable_contraction_sequence_optimization()` and `ITensors.disable_contraction_sequence_optimization()`.

For a custom sequence, the sequence should be provided as a binary tree where the leaves are integers `n` specifying the ITensor `As[n]` and branches are accessed by indexing with `1` or `2`, i.e. `sequence = Any[Any[1, 3], Any[2, 4]]`.
