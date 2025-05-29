```
MultiRBFE(v::AbstractVector, nc; normalize=false, coulomb=false)
```

供給スケジューリング信号 `v` と中心の数 `nc` K-meansを使用して共分散行列と中心を自動的に選択します。

キーワード `normalize` は、基底関数の活性化が各データポイントの合計が1になるように正規化されるかどうかを決定します。正規化されたネットワークは、外挿がより良くなる傾向があります ["The normalized radial basis function neural network" DOI: 10.1109/ICSMC.1998.728118](http://ieeexplore.ieee.org/document/728118/)
