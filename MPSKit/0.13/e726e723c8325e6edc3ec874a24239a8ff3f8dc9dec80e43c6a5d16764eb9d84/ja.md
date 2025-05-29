```
MPOHamiltonian(lattice::AbstractArray{<:VectorSpace}, local_operators...)
MPOHamiltonian(lattice::AbstractArray{<:VectorSpace})
MPOHamiltonian(x::AbstractArray{<:Any,3})
```

ハミルトニアンのMPO表現。これは、すべてのサイトが次の形式の上三角ブロック行列で表される[`AbstractMPO`](@ref)の特定の形です：

$$
\begin{pmatrix}
1 & C & D \\
0 & A & B \\
0 & 0 & 1
\end{pmatrix}
$$

ここで、`A`、`B`、`C`、および`D`は`MPOTensor`、またはその（スパース）ブロックです。

## 例

たとえば、最近接隣接ハミルトニアンを構築する場合は、次のようになります：

```julia
lattice = fill(ℂ^2, 10)
H = MPOHamiltonian(lattice, (i, i+1) => O for i in 1:length(lattice)-1)
```

このコンストラクタと互換性のある形式でローカルオペレーターをインスタンス化する責任を持つ[`instantiate_operator`](@ref)も参照してください。
