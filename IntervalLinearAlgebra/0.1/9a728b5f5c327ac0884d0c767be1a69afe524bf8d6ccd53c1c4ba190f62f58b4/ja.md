```
InverseMidpoint <: AbstractPrecondition
```

線形システム $Ax=b$ を $A_c^{-1}$ で前処理する前処理器であり、ここで $A_c$ は $A$ の中点行列です。

### 注意事項

  * `InverseMidpoint` 型のオブジェクトは、次のメソッドを持つ関数です。

    ```
      (imp::InverseMidpoint)(A::AbstractMatrix{T},
                             b::AbstractVector{T}) where {T<:Interval}
    ```

### 例

```jldoctest
julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> b = [-2..2, -2..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]

julia> imp = InverseMidpoint()
InverseMidpoint()

julia> imp(A, b)
(Interval{Float64}[[0.594594, 1.40541] [-0.540541, 0.540541]; [-0.540541, 0.540541] [0.594594, 1.40541]], Interval{Float64}[[-0.756757, 0.756757], [-0.756757, 0.756757]])
```
