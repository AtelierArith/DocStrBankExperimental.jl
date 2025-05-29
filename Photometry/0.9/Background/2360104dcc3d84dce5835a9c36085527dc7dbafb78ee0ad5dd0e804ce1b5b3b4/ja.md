```
MADStdRMS()
```

標準的な中央値絶対偏差（MAD）統計量を使用して、背景RMSの推定を行います。

これは通常次のように表されます。

$$
σ ≈ 1.4826 ⋅ \mathrm{MAD}
$$

# 例

```jldoctest
julia> data = ones(3, 5);

julia> MADStdRMS()(data)
0.0

julia> MADStdRMS()(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
