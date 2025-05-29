```
InverseDiagonalMidpoint <: AbstractPrecondition
```

線形システム $Ax=b$ を、$A_c$ の対角行列 $A_c^{-1}$ で前処理する前処理器です。ここで、$A_c$ は $A$ の中点行列です。

### 注意事項

  * `InverseDiagonalMidpoint` 型のオブジェクトは、次のメソッドを持つ関数です。

    ```
      (idmp::InverseDiagonalMidpoint)(A::AbstractMatrix{T},
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

julia> idmp = InverseDiagonalMidpoint()
InverseDiagonalMidpoint()

julia> idmp(A, b)
(Interval{Float64}[[0.666666, 1.33334] [-0.666667, 0.333334]; [-0.333334, 0.666667] [0.666666, 1.33334]], Interval{Float64}[[-0.666667, 0.666667], [-0.666667, 0.666667]])
```
