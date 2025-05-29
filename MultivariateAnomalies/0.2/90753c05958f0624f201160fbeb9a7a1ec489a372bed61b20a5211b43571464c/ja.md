```
kernel_matrix(D::AbstractArray, σ::Float64 = 1.0[, kernel::String = "gauss", dimension::Int64 = 1])
```

距離行列 `D` からカーネル行列を計算し、`σ` を指定します。オプションで、`kernel = "normalized_gauss"` の場合は `dimension` で正規化されます。`D` は `dist_matrix()` で計算します。

# 例

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> K = kernel_matrix(D, 2.0)
```
