```
NoPrecondition <: AbstractPrecondition
```

何もしないトリビアル前処理器の型です。

### 注意事項

  * `NoPrecondition` 型のオブジェクトは、次のメソッドを持つ関数です。

    ```
      (np::NoPrecondition)(A::AbstractMatrix{T},
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

julia> np = NoPrecondition()
NoPrecondition()

julia> np(A, b)
(Interval{Float64}[[2, 4] [-2, 1]; [-1, 2] [2, 4]], Interval{Float64}[[-2, 2], [-2, 2]])
```
