```
VolumePreservingUpperLayer(dim)
```

特定のシステム次元のために `VolumePreservingUpperLayer` のインスタンスを作成します。

[`VolumePreservingFeedForwardLayer`](@ref) のドキュメントを参照してください。

# 例

行列を用いて `VolumePreservingUpperLayer` を適用します：

$$
U = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}
$$

ベクトルに対して：

$$
x = \begin{pmatrix} 1 \\ 1 \end{pmatrix}
$$

```jldoctest
using GeometricMachineLearning

l = VolumePreservingUpperLayer(2, identity; use_bias=false)
A = UpperTriangular([1,], 2)
ps = (weight = A, )
x = ones(eltype(A), 2)

l(x, ps)

# output

2×1 Matrix{Int64}:
 2
 1
```

# 引数

コンストラクタはオプションの引数で呼び出すことができます：

  * `activation=tanh`: 活性化関数。
  * `use_bias::Bool=true` (キーワード引数): バイアスを使用するかどうかを指定します。
