```
S0Graph(sig::AlgebraShape, S::Subspace{ComplexF64, 2})

S0Graph(g::AbstractGraph)
```

arxiv:1002.2514で定義されたS₀-グラフを表します。

  * `n::Integer`: S ⊆ L(A)となるヒルベルト空間Aの次元
  * `sig::Matrix{<:Integer}`: C*-代数S₀の構造
  * `S::Subspaces.Subspace{ComplexF64, 2}`: グラフを定義する部分空間
  * `S0::Subspaces.Subspace{ComplexF64, 2}`: C*-代数S₀
  * `S1::Subspaces.Subspace{ComplexF64, 2}`: C*-代数S₀の共役
  * `D::Matrix{Float64}`: arxiv:2101.00162の定義23からのブロックスケーリング配列D
