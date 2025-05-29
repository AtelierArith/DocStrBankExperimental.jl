```
kernel_matrix!(K, D::AbstractArray, σ::Float64 = 1.0[, kernel::String = "gauss", dimension::Int64 = 1])
```

距離行列 `D` からカーネル行列を計算します。`kernel_matrix()` と似ていますが、出力用に事前に割り当てられた配列 K (`K = similar(D)`) を使用します。

# 例

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> kernel_matrix!(D, D, 2.0) # 距離行列を上書きします
```
