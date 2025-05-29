```
 inducingpoints([rng::AbstractRNG], alg::OIPS, X::AbstractVector; kernel::Kernel)
 inducingpoints([rng::AbstractRNG], alg::OIPS, X::AbstractMatrix; obsdim=1, kernel::Kernel)
```

オンライン誘導点選択を使用して誘導点を選択します。追加のキーワード引数として `kernel` が必要です。
