```
 inducingpoints([rng::AbstractRNG], alg::SeqDPP, X::AbstractVector; kernel::Kernel)
 inducingpoints([rng::AbstractRNG], alg::SeqDPP, X::AbstractMatrix; obsdim=1, kernel::Kernel)
```

逐次決定論的点過程を使用して誘導点を選択します。キーワード引数として `kernel::Kernel` を渡す必要があります。
