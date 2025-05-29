```
LinearOettliPrager <: AbstractDirectSolver
```

区間線形システム $Ax=b$ の OettliPrager ソルバーの型です。ソルバーは最初に、Oettli-Präger 定理 [[OET64]](@ref) を使用して、区間等式のシステムを実数不等式のシステムに変換し、その後、`LazySets.jl` を使用して各オルタンで LP 問題を解くことによって実行可能な集合を見つけます。

### 注意事項

  * この機能を使用するには `LazySets.jl` をインポートする必要があります。
  * `LinearOettliPrager` 型のオブジェクトは、以下のメソッドを持つ関数です。

    ```
      (op::LinearOettliPrager)(A::AbstractMatrix{T},
                               b::AbstractVector{T}) where {T<:Interval}
    ```

    #### 入力

      * `A`   – N×N 区間行列
      * `b`   – 長さ N の区間ベクトル

### 例

```julia-repl
julia> A = [2..4 -2..1;-1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> b = [-2..2, -2..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]

julia> polytopes = solve(A, b, LinearOettliPrager());

julia> typeof(polytopes)
Vector{HPolytope{Float64, SparseArrays.SparseVector{Float64, Int64}}}
```
