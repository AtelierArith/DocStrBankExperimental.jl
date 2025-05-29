```
UniformRBFE(v::Vector, Nv::Int; normalize=false, coulomb=false)
```

供給スケジューリング信号と基底関数の数 自動的に中心と幅を選択するため

キーワード `normalize` は、基底関数の活性化が各データポイントの合計が1になるように正規化されるかどうかを決定します。正規化されたネットワークは、より良い外挿を行う傾向があります ["The normalized radial basis function neural network" DOI: 10.1109/ICSMC.1998.728118](http://ieeexplore.ieee.org/document/728118/)
