```
mul!(C::AbstractVecOrMat, A::LinearMap, B::AbstractVector, α, β) -> C
mul!(C::AbstractMatrix, A::LinearMap, B::AbstractMatrix, α, β) -> C
```

結合されたインプレースの乗算加算 $A B α + C β$。結果は `C` に上書きされて保存されます。`C` は `A` または `B` とエイリアスされてはいけません。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); B=[1.0, 1.0]; C=[1.0, 3.0];

julia> mul!(C, A, B, 100.0, 10.0) === C
true

julia> C
2-element Vector{Float64}:
 310.0
 730.0

julia> A=LinearMap([1.0 2.0; 3.0 4.0]); B=[1.0 1.0; 1.0 1.0]; C=[1.0 2.0; 3.0 4.0];

julia> mul!(C, A, B, 100.0, 10.0) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0
```
