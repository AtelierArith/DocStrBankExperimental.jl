```
contract_ncon_indices(tn::TensorNetwork, A_sym::Symbol, B_sym)
```

Function return indices in ncon format for contraction of tensors with given symbols. Returns two tuples for indices in each with convention that negative values are remaining indices and positive values are indices being contracted over.

For example if (1, -1), (-2, 1) is returned, this menas that the first index of tensor A A is contracted with the second index of  tensor B and the resulting tensor will have indices corresponding to the second index of the first tensor and first index of the second tensor.
