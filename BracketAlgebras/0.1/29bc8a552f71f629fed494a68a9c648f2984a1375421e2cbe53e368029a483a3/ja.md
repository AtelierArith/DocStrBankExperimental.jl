```
BracketAlgebraElem{T<:Union{RingElem,Number}} <: AbstractBracketAlgebraElem{T}
```

[`BracketAlgebra`](@ref) の要素型で、係数の型は `T` です。

# フィールド

  * `parent::BracketAlgebra{T}`: ブラケット代数要素の親オブジェクト。
  * `polynomial::MPolyRingElem{T}`: 要素を表す `parent.R` の多項式。
