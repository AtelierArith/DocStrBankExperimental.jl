```
statdists(hmm) -> Vector{Vector}
```

`hmm`の定常分布を返します。すなわち、固有値が1のtranspose(hmm.A)の固有ベクトルです。
