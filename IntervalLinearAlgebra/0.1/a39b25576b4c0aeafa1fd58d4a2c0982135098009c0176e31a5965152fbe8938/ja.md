```
HansenBliekRohn <: AbstractDirectSolver
```

平方区間線形システム $Ax=b$ の `HansenBliekRohn` ソルバーの型。詳細については [[HOR19]](@ref) のセクション 5.6.2 を参照してください。

### ノート

  * Hansen-Bliek-Rohn は前処理なしで H-行列と、[`InverseMidpoint`](@ref) 前処理を使用した強正則行列で動作します。
  * $$
    A
    $$

    の中点が対角行列である場合、アルゴリズムは正確なハルを返します。
  * Hansen-Bliek-Rohn 型のオブジェクトは、次のメソッドを持つ呼び出し可能な関数です。

    ```
      (hbr::HansenBliekRohn)(A::AbstractMatrix{T},
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

julia> hbr = HansenBliekRohn()
HansenBliekRohn linear solver

julia> hbr(A, b)
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
