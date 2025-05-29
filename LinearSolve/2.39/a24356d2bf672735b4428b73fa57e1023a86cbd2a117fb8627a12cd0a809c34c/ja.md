```julia
MKLLUFactorization()
```

IntelのMath Kernel Library (MKL) のラッパーです。ワークスペースを事前に割り当ててアロケーションを回避し、libblastrampolineを必要としない形でMKLに直接呼び出します。
