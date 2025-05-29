```
dim(t::AbstractTensorMap) -> Int
```

テンソルの自由パラメータの総数であり、対称性によって固定されているエントリは考慮しません。これは、`TensorMap` が定義されている `HomSpace` の次元でもあります。
