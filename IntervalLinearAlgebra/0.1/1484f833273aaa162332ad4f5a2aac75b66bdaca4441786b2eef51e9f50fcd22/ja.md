```
NonLinearOettliPrager <: AbstractIterativeSolver
```

区間線形システム $Ax=b$ の OettliPrager ソルバーの型です。ソルバーはまず、Oettli-Präger 定理 [[OET64]](@ref) を使用して区間等式のシステムを実数不等式のシステムに変換し、その後、`IntervalConstraintProgramming.jl` に実装された前方-後方コントラクタ法 [[JAU14]](@ref) を使用して実行可能な集合を見つけます。

### フィールド

  * `tol` – パビングの許容誤差、デフォルトは 0.01。

### 注意事項

  * この機能を使用するには `IntervalConstraintProgramming.jl` をインポートする必要があります。
  * `NonLinearOettliPrager` 型のオブジェクトは、以下のメソッドを持つ関数です。

    ```
      (op::NonLinearOettliPrager)(A::AbstractMatrix{T},
                                  b::AbstractVector{T},
                                  [X]::AbstractVector{T}=enclose(A, b)) where {T<:Interval}

      (op::NonLinearOettliPrager)(A::AbstractMatrix{T},
                                  b::AbstractVector{T},
                                  X::IntervalBox) where {T<:Interval}
    ```

    #### 入力

      * `A`   – N×N 区間行列
      * `b`   – 長さ N の区間ベクトル
      * `X`   – （オプション）$Ax = b$ の解の初期エンクロージャ。指定されていない場合は、[`enclose`](@ref enclose) を使用して自動的に計算されます。

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

julia> solve(A, b, NonLinearOettliPrager(0.1))
Paving:
- tolerance ϵ = 0.1
- inner approx. of length 1195
- boundary approx. of length 823
```
