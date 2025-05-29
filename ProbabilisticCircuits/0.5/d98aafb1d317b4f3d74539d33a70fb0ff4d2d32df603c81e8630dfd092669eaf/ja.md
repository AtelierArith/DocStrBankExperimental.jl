```
mini_batch_em(bpc::CuBitsProbCircuit, raw_data::CuArray, num_epochs; batch_size, pseudocount,
    param_inertia, param_inertia_end = param_inertia, shuffle=:each_epoch)
```

CuBitsProbCircuitのパラメータをEMを行うことで更新し、各バッチの後にパラメータを更新します。
