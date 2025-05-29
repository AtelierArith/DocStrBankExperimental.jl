```
solve(A::AbstractMatrix{T},
      b::AbstractVector{T},
      solver::AbstractDirectSolver,
      [precondition]::AbstractPrecondition=_default_precondition(A, solver)) where
      {T<:Interval}
```

与えられたアルゴリズム、前処理器、および初期エンクロージャを使用して、平方区間システム $Ax=b$ を解きます。

### 入力

  * `A` – 平方区間行列
  * `b` – 区間ベクトル
  * `solver` – 線形システムを解くために使用されるアルゴリズム
  * `precondition` – 使用される前処理器。指定されていない場合、行列 `A` とソルバーに基づいて自動的に計算されます。

### 例

```jldoctest
julia> A = [2..4 -1..1;-1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> b = [-2..2, -1..1]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-1, 1]

julia> solve(A, b, HansenBliekRohn(), InverseMidpoint())
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]

julia> solve(A, b, HansenBliekRohn())
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
