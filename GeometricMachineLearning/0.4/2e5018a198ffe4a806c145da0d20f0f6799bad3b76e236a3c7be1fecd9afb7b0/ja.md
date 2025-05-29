```
PoissonTensor(n2)
```

サイズ $2n\times2n$ の（標準的な）ポアソンテンソルを返します：

$$
\mathbb{J}_{2n} = \begin{pmatrix}
\mathbb{O} & \mathbb{I}_n \\
-\mathbb{I}_n & \mathbb{O} \\
\end{pmatrix}
$$

# 引数

`backend` と `type` を指定して呼び出すこともできます：

```jldoctest
using GeometricMachineLearning

backend = CPU()
T = Float16

PoissonTensor(backend, 4, T)

# 出力

4×4 PoissonTensor{Float16, Matrix{Float16}}:
  0.0   0.0  1.0  0.0
  0.0   0.0  0.0  1.0
 -1.0   0.0  0.0  0.0
  0.0  -1.0  0.0  0.0
```
