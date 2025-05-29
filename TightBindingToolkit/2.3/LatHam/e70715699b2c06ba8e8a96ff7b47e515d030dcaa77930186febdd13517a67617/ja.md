`LatticeHamiltonian` は、`Lattice` オブジェクトを使用して構築された一般的な実空間ハミルトニアンを表すデータ型です。

# 属性

  * `H           ::      Matrix{ComplexF64}`: ハミルトニアン行列。
  * `bands       ::      Vector{Float64}`: ハミルトニアンの固有値。
  * `states      ::      Matrix{ComplexF64}`: ハミルトニアンの固有ベクトル。
  * `is_BdG      ::      Bool`: ハミルトニアンが BdG ハミルトニアンであるかどうか。
  * `bandwidth   ::      Tuple{Float64, Float64}`: ハミルトニアンの最小および最大固有値。

この構造体は次のように初期化します。

```julia
LatticeHamiltonian( lattice::Lattice{2} )
```
