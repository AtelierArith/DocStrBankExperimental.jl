```
VolumePreservingLowerLayer(dim)
```

特定のシステム次元のために `VolumePreservingLowerLayer` のインスタンスを作成します。

[`VolumePreservingFeedForwardLayer`](@ref) のドキュメントを参照してください。

# 例

行列を用いて `VolumePreservingLowerLayer` を適用します：

$$
L = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}
$$

ベクトルに対して：

$$
x = \begin{pmatrix} 1 \\ 1 \end{pmatrix}
$$

```jldoctest
using GeometricMachineLearning

l = VolumePreservingLowerLayer(2, identity; use_bias=false)
A = LowerTriangular([1,], 2)
ps = (weight = A, )
x = ones(eltype(A), 2)

l(x, ps)

# output

2×1 Matrix{Int64}:
 1
 2
```

# 引数

コンストラクタはオプションの引数で呼び出すことができます：

  * `activation=tanh`: 活性化関数。
  * `use_bias::Bool=true` (キーワード引数): バイアスを使用するかどうかを指定します。
