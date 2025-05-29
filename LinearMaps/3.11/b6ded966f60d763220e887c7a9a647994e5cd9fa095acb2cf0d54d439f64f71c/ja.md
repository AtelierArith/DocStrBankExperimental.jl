```
mul!(C::AbstractMatrix, A::AbstractMatrix, B::LinearMap, α, β) -> C
```

インプレースでの乗算加算 $A B α + C β$ を組み合わせます。結果は `C` に上書きされて保存されます。`C` は `A` または `B` とエイリアスされてはいけません。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=[1.0 1.0; 1.0 1.0]; B=LinearMap([1.0 2.0; 3.0 4.0]); C = copy(A);

julia> mul!(C, A, B, 1, 1)
2×2 Matrix{Float64}:
 5.0  7.0
 5.0  7.0
```
