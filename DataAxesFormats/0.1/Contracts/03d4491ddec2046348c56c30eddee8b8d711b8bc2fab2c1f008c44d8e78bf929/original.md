```
verify_output(contract_daf::ContractDaf)::Nothing
```

Verify the `contract_daf` data when a computation is complete. This verifies that all the guaranteed output data exists and is of the appropriate type, and that if any of the optional output data exists, it has the appropriate type. It also verifies that all the required inputs were accessed by the computation.
