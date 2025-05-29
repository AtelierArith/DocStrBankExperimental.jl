```
full_batch_em(bpc::CuBitsProbCircuit, raw_data::CuArray, num_epochs; batch_size, pseudocount)
```

Update the paramters of the CuBitsProbCircuit by doing EM on the full batch (i.e. update paramters at the end of each epoch).
