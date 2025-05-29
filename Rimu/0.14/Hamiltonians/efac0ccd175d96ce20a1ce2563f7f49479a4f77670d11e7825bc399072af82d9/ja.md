```
GuidingVectorSampling
```

任意の [`AbstractHamiltonian`](@ref) をラップし、ガイディングベクトル、すなわちガイディング波動関数サンプリングを実装します。この重要度サンプリングスキームでは、ハミルトニアンが次のように修正されます。

$$
\tilde{H}_{ij} = v_i H_{ij} v_j^{-1}
$$

ここで `v` はガイディングベクトルです。`v_i` と `v_j` はゼロで割るのを避けるためにしきい値処理されます（下記参照）。

# コンストラクタ

  * `GuidingVectorSampling(::AbstractHamiltonian, vector, eps)`
  * `GuidingVectorSampling(::AbstractHamiltonian; vector, eps)`

`eps` はゼロで割るのを避けるために使用されるしきい値パラメータで、`eps` 未満のすべての値は `eps` に設定されます。`eps` はガイディングベクトルと同じ値範囲にあることが推奨されます。デフォルト値は `eps=norm(v, Inf) * 1e-2` に設定されています。

構築後、`G.hamiltonian` で基礎となるハミルトニアンにアクセスでき、`G.eps` で `eps` パラメータに、`G.vector` でガイディングベクトルにアクセスできます。

# 例

```jldoctest
julia> H = HubbardReal1D(BoseFS(1,1,1); u=6.0, t=1.0);

julia> v = DVec(starting_address(H) => 10; capacity=1);

julia> G = GuidingVectorSampling(H, v, 0.1);

julia> get_offdiagonal(H, starting_address(H), 4)
(BoseFS{3,3}(2, 0, 1), -1.4142135623730951)

julia> get_offdiagonal(G, starting_address(G), 4)
(BoseFS{3,3}(2, 0, 1), -0.014142135623730952)
```

# 観測量

観測量を計算するには、変換されたハミルトニアン `G` を [`AllOverlaps`](@ref) にキーワード引数 `transform=G` と共に渡します。
