```
GaussianElimination <: AbstractDirectSolver
```

平方区間線形システム $Ax=b$ のガウス消去ソルバーの型。詳細については[[HOR19]](@ref)のセクション5.6.1を参照してください。

### ノート

  * `GaussianElimination` 型のオブジェクトは、次のメソッドを持つ呼び出し可能な関数です。

    ```
      (ge::GaussianElimination)(A::AbstractMatrix{T},
                                b::AbstractVector{T}) where {T<:Interval}
    ```

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

julia> ge = GaussianElimination()
GaussianElimination linear solver

julia> ge(A, b)
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
