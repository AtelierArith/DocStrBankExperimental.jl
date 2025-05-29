```
standard_uniformization(Q, k=2^10, t=0.0, ϵ=10e-9; p0)
```

標準一様化を使用して、ポアソン分布の左切断および右切断を用いて、時間 t までのジャンプ数を近似し、𝐩(t) = exp(t𝐐)𝐩(0) を近似します。左切断点と右切断点を選択するルールは、Reibman & Trivedi (1988, Computers & Operations Research) に基づいています。

これは、𝐩(t) をその場で計算することに注意してください。erlangization() や discrete*observation*() のように行列 𝐑(t) を返すことはありません。
