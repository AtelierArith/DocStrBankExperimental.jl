```
mul!(C::AbstractMatrix, A::AbstractMatrix, B::LinearMap) -> C
```

`A*B`の行列表現を計算し、結果を`C`に格納します。これにより、`C`の既存の値が上書きされます。`C`は`A`または`B`とエイリアスされてはいけません。計算`C = A*B`は`C' = B'A'`を介して行われます。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=[1.0 1.0; 1.0 1.0]; B=LinearMap([1.0 2.0; 3.0 4.0]); C = similar(A); mul!(C, A, B);

julia> C
2×2 Matrix{Float64}:
 4.0  6.0
 4.0  6.0
```
