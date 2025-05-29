```
AbstractHamiltonian{T} <: AbstractOperator{T}
```

FCIQMCに適したスカラー型`T`の線形空間上の線形演算子のインターフェースを提供するスーパークラスです（[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)を参照）。インデックス付けは、通常は整数ではないアドレス空間からのアドレスを使用して行われ、アドレス空間は大きくなる可能性があり（完全に生成する必要はありません）。

`AbstractHamiltonian`のインスタンスは、モジュール`DictVectors`の型[`AbstractDVec`](@ref)のベクトル上で動作し、モジュール`BitStringAddresses`の型[`AbstractFockAddress`](@ref Main.BitStringAddresses.AbstractFockAddress)のアドレスともうまく機能します。この型は、外部パッケージ[KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl)ともよく機能します。

利用可能な実装については、[`Hamiltonians`](@ref Main.Hamiltonians)を参照してください。

# インターフェース

実装する基本的なインターフェースメソッド：

  * [`starting_address(::AbstractHamiltonian)`](@ref)
  * [`diagonal_element(::AbstractHamiltonian, address)`](@ref)
  * [`num_offdiagonals(::AbstractHamiltonian, address)`](@ref)
  * [`get_offdiagonal(::AbstractHamiltonian, address, chosen::Integer)`](@ref)（オプション、以下を参照）

実装するオプションの追加メソッド：

  * [`LOStructure(::Type{typeof(lo)})`](@ref LOStructure): デフォルトは`AdjointUnknown`
  * [`dimension(::AbstractHamiltonian, addr)`](@ref Main.Hamiltonians.dimension): デフォルトはアドレス空間の次元
  * [`allows_address_type(h::AbstractHamiltonian, type)`](@ref): デフォルトは`type :< typeof(starting_address(h))`
  * [`momentum(::AbstractHamiltonian)`](@ref Main.Hamiltonians.momentum): デフォルトなし

以下の関数とメソッドを提供します：

  * [`offdiagonals`](@ref): 到達可能なオフダイアゴナル行列要素のイテレータ
  * [`random_offdiagonal`](@ref): ランダムなオフダイアゴナル行列要素を生成する関数
  * `*(H, v)`: 決定論的な行列-ベクトルの乗算（アロケーションあり）
  * `H(v)`: `H * v`に相当します。
  * `mul!(w, H, v)`: 変異する行列-ベクトルの乗算。
  * [`dot(x, H, v)`](@ref Main.Hamiltonians.dot): アロケーションを最小限に抑えて`x⋅(H*v)`を計算します。
  * `H[address1, address2]`: `getindex()`によるインデックス付け - 主にテスト目的（遅い！）
  * [`BasisSetRepresentation`](@ref Main.ExactDiagonalization.BasisSetRepresentation): 基底集合の表現を構築
  * [`sparse`](@ref Main.ExactDiagonalization.sparse), [`Matrix`](@ref): （スパース）行列表現を構築

上記の代わりに、[`offdiagonals`](@ref)を[`get_offdiagonal`](@ref)の代わりに実装することができます。場合によっては、これを効率的に行うことができます。この場合、[`num_offdiagonals`](@ref)は、[`offdiagonals`](@ref)を反復する際に得られる要素の数の上限を提供する必要があります。

また、[`Hamiltonians`](@ref Main.Hamiltonians)、[`Interfaces`](@ref)、[`AbstractOperator`](@ref)、[`AbstractObservable`](@ref)も参照してください。
