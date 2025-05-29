```
predict(M::PCA, x::AbstractVecOrMat{<:Real})
```

PCAモデル`M`が与えられたとき、観測値`x`を主成分空間に変換します。次のように、

$$
\mathbf{y} = \mathbf{P}^T (\mathbf{x} - \boldsymbol{\mu})
$$

ここで、`x`は長さ`d`のベクトルまたは各列が観測値である行列のいずれかであり、`\mathbf{P}`は射影行列です。
