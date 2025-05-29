```
AbstractOperator{T} <: AbstractObservable{T}
```

線形空間の型 `T`（[`eltype`](@ref) によって返される）を持つ要素に対する線形演算子のインターフェースを提供するスーパークラス。

`AbstractOperator` のインスタンスは、モジュール `DictVectors` からの型 [`AbstractDVec`](@ref) のベクトルに作用し、モジュール `BitStringAddresses` からの型 [`AbstractFockAddress`](@ref Main.BitStringAddresses.AbstractFockAddress) のアドレスともうまく機能します。

`AbstractOperator` の定義的な特徴は、[`mul!(y, op, x)`](@ref LinearAlgebra.mul!) を使用してベクトルに適用でき、[`dot(x, op, y)`](@ref LinearAlgebra.dot) を使用して三項ドット積を計算できることです。

`AbstractOperator` 型は、必ずしもハミルトニアンである必要はない演算子を定義するのに便利ですが、[`ProjectorMonteCarloProblem`](@ref) の文脈で観測可能な演算子として [`ReplicaStrategy`](@ref Rimu.ReplicaStrategy) で使用できます。例えば、相関関数を定義するために使用されます。[`AbstractHamiltonian`](@ref)s と対照的に、`AbstractOperator` は [`starting_address`](@ref) を持つ必要はありません。さらに、`AbstractOperator` の `eltype` はベクトル値であることができ、[`AbstractHamiltonian`](@ref)s はスカラーの `eltype` を必要とします。

```
AbstractHamiltonian{T} <: AbstractOperator{T} <: AbstractObservable{T}
```

`AbstractOperator` 型は [`AbstractObservable`](@ref) 階層の一部です。対角要素と非対角要素の生成のためのインターフェースを要求する点で、`AbstractObservable` よりも制約が厳しいです。

具体的な実装については、[`Hamiltonians`](@ref Main.Hamiltonians) を参照してください。[`ProjectorMonteCarloProblem`](@ref) または [`ExactDiagonalizationProblem`](@ref) で使用するためのハミルトニアンを実装するには、代わりに型 [`AbstractHamiltonian`](@ref) を使用してください。

# インターフェース

実装する基本インターフェースメソッド：

  * [`allows_address_type(op, type)`](@ref)
  * [`diagonal_element(op, address)`](@ref)
  * [`num_offdiagonals(op, address)`](@ref) および
  * [`get_offdiagonal(op, address, chosen)`](@ref) または [`offdiagonals`](@ref)

実装するオプションの追加メソッド：

  * [`VectorInterface.scalartype(op)`](@ref): デフォルトは `eltype(eltype(op))`
  * [`LOStructure(::Type{typeof(op)})`](@ref LOStructure): デフォルトは `AdjointUnknown`
  * [`dimension(op, addr)`](@ref Main.Hamiltonians.dimension): デフォルトはアドレス空間の次元

観測可能なものを効率的に計算するために、[`Interfaces.dot_from_right(x, op, y)`](@ref) および [`LinearAlgebra.mul!(y, op, x)`](@ref) のカスタムメソッドを実装することが理にかなう場合があります。

[`AbstractHamiltonian`](@ref)、[`Interfaces`](@ref) も参照してください。
