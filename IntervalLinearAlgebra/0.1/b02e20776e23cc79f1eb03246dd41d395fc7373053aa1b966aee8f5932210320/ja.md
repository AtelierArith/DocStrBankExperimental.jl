```
LinearKrawczyk <: AbstractIterativeSolver
```

区間線形システム $Ax=b$ のための Krawczyk ソルバーの型。詳細は [[HOR19]](@ref) のセクション 5.7.3 を参照。

### フィールド

  * `max_iterations` – 最大反復回数 (デフォルト 20)
  * `atol`           – 絶対許容誤差 (デフォルト 0)、ある時点で $|xₖ - xₖ₊₁| < atol$                     （要素ごとに）、その場合は停止して $xₖ₊₁$ を返す。                     `atol=0` の場合、`min(diam(A))*1e-5` が使用される。

### 注意事項

  * `LinearKrawczyk` 型のオブジェクトは、次のメソッドを持つ関数です。

    ```
      (kra::LinearKrawczyk)(A::AbstractMatrix{T},
                            b::AbstractVector{T},
                            [x]::AbstractVector{T}=enclose(A, b)) where {T<:Interval}
    ```

    #### 入力

      * `A`   – N×N 区間行列
      * `b`   – 長さ N の区間ベクトル
      * `x`   – （オプション）$Ax = b$ の解の初期エンクロージャ。指定されていない場合、          [`enclose`](@ref enclose) を使用して自動的に計算される。

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

julia> kra = LinearKrawczyk()
LinearKrawczyk linear solver
max_iterations = 20
atol = 0.0

julia> kra(A, b)
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]
```
