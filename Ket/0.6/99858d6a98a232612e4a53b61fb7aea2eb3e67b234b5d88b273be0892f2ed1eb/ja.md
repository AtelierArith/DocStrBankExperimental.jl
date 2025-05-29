```
conditional_entropy([base=2,], rho::AbstractMatrix, csys::AbstractVecOrTuple, dims::AbstractVecOrTuple)
```

`rho`の条件付きvon Neumannエントロピーを、サブシステムの次元`dims`と条件付けシステム`csys`を使用して、基数`base`の対数を用いて計算します。

参考文献: [条件付き量子エントロピー](https://en.wikipedia.org/wiki/Conditional_quantum_entropy)
