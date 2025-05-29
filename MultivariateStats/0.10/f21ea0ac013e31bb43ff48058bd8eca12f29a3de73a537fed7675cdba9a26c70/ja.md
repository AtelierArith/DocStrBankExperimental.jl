```
reconstruct(M::PCA, y::AbstractVecOrMat{<:Real})
```

PCAモデル`M`が与えられたとき、主成分空間から（おおよそ）再構成された観測値を返します。これは次のように表されます。

$$
\tilde{\mathbf{x}} = \mathbf{P} \mathbf{y} + \boldsymbol{\mu}
$$

ここで、`y`は長さ`p`のベクトルまたは各列が観測の主成分を与える行列であり、$\mathbf{P}$は射影行列です。
