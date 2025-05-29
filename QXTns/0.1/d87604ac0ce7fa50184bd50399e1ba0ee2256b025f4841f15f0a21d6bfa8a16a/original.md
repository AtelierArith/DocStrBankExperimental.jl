```
contract_pair!(tn::TensorNetwork, A_id::Symbol, B_id::Symbol; mock::Bool=false)
```

Contract the tensors in 'tn' with ids 'A*id' and 'B*id'. If the mock flag is true then the new tensor will be a mock tensor with the right dimensions but without the actual data.

The resulting tensor is stored in `tn` under the symbol `C_id` if one is provided, otherwise a new id is created for it.
