```julia
random_matrix_product_state(
    ::Type{T},
    n::Int64,
    chi::Int64
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}
random_matrix_product_state(
    ::Type{T},
    n::Int64,
    chi::Int64,
    d::Int64
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

行列積状態（MPS）は、量子多体物理学で広く使用されるテンソルネットワークモデルです。これは、テンソルがランク3のテンソルであり、物理インデックスがチェーンで接続されているテンソルネットワークモデルの特別なケースです。MPSは次のように定義されます：

$$
\begin{align*}
\left| \psi \right\rangle &= \sum_{x_1, x_2, \ldots, x_n} \text{Tr}(A_1^{x_1} A_2^{x_2} \cdots A_n^{x_n}) \left| x_1, x_2, \ldots, x_n \right\rangle \\
\left\langle \psi \right| &= \sum_{x_1, x_2, \ldots, x_n} \text{Tr}(A_n^{x_n} \cdots A_2^{x_2} A_1^{x_1}) \left\langle x_1, x_2, \ldots, x_n \right|
\end{align*}
$$

ここで、$A_i^{x_i}$は物理インデックス$x_i$と次のテンソルに接続する2つの仮想インデックスを持つランク3のテンソルです。MPSは、テンソルがランク3のテンソルであり、物理インデックスがチェーンで接続されているテンソルネットワークモデルの特別なケースです。

### 引数

  * `n`は物理インデックスの数です。
  * `chi`は仮想インデックスのボンド次元です。
  * `d`は物理インデックスの次元です。
