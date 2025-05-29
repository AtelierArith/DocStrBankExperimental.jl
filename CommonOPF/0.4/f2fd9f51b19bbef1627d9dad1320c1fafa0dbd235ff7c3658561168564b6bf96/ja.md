```
Yij(i::AbstractString, j::AbstractString, net::CommonOPF.Network)::Union{ComplexF64, Matrix{ComplexF64}}
```

次のいずれかを返します：

  * 単相ネットワークのi,jにおけるアドミタンス行列のエントリ、または
  * バスiとjを接続する位相のための3x3アドミタンスサブマトリックス
