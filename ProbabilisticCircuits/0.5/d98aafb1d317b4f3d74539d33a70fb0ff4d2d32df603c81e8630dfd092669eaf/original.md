```
mini_batch_em(bpc::CuBitsProbCircuit, raw_data::CuArray, num_epochs; batch_size, pseudocount,
    param_inertia, param_inertia_end = param_inertia, shuffle=:each_epoch)
```

Update the parameters of the CuBitsProbCircuit by doing EM, update the parameters after each batch.
