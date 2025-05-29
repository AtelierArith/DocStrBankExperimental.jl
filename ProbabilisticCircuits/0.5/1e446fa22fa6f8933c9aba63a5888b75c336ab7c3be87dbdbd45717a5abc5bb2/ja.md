```
full_batch_em(bpc::CuBitsProbCircuit, raw_data::CuArray, num_epochs; batch_size, pseudocount)
```

フルバッチでEMを行うことによってCuBitsProbCircuitのパラメータを更新します（すなわち、各エポックの終わりにパラメータを更新します）。
