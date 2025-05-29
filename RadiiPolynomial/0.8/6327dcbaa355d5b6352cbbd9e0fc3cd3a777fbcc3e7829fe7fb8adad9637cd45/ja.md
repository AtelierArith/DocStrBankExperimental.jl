```
LinearOperator{T<:VectorSpace,S<:VectorSpace,R<:AbstractMatrix}
```

効果的な定義域と値域を持つコンパクトサポート線形演算子。

フィールド:

  * `domain :: T`
  * `codomain :: S`
  * `coefficients :: R`

コンストラクタ:

  * `LinearOperator(::VectorSpace, ::VectorSpace, ::AbstractMatrix)`
  * `LinearOperator(coefficients::AbstractMatrix)`: `LinearOperator(ParameterSpace()^size(coefficients, 2), ParameterSpace()^size(coefficients, 1), coefficients)` と同等

# 例

```jldoctest
julia> LinearOperator(Taylor(1), Taylor(1), [1 2 ; 3 4])
LinearOperator : Taylor(1) → Taylor(1) with coefficients Matrix{Int64}:
 1  2
 3  4

julia> LinearOperator(Taylor(2), ParameterSpace(), [1.0 0.5 0.25])
LinearOperator : Taylor(2) → 𝕂 with coefficients Matrix{Float64}:
 1.0  0.5  0.25

julia> LinearOperator([1 2 3 ; 4 5 6])
LinearOperator : 𝕂³ → 𝕂² with coefficients Matrix{Int64}:
 1  2  3
 4  5  6
```
