```
AbstractObservable{T}
```

型階層における演算子の最も許容範囲の広いスーパタイプ：

```
AbstractHamiltonian{T} <: AbstractOperator{T} <: AbstractObservable{T}
```

`AbstractObservable` は、二つの [`AbstractDVec`](@ref) 型のベクトルとの三項ドット積 [`dot(x, op, y)`](@ref LinearAlgebra.dot) に現れることができる演算子のインターフェースを提供します。結果は型 `T` の値であり、これは [`eltype`](@ref) 関数によっても返されます。これは、[`scalartype`](@ref) 関数によって返されるスカラー型に関連付けられたベクトル型である可能性があります。

`AbstractObservable` 型は、[`AllOverlaps`](@ref Main.Hamiltonians) を使用して [`ProjectorMonteCarloProblem`](@ref) の文脈で計算できる可観測量を定義するのに役立ちます。

# インターフェース

実装する基本インターフェースメソッド：

  * [`Interfaces.dot_from_right(x, op, y)`](@ref)
  * [`allows_address_type(op, type)`](@ref)

実装するオプションの追加メソッド：

  * [`VectorInterface.scalartype(op)`](@ref): デフォルトは `eltype(eltype(op))`
  * [`LOStructure(::Type{typeof(op)})`](@ref LOStructure): デフォルトは `AdjointUnknown`

さらに [`AbstractOperator`](@ref)、[`AbstractHamiltonian`](@ref)、[`Interfaces`](@ref) も参照してください。
