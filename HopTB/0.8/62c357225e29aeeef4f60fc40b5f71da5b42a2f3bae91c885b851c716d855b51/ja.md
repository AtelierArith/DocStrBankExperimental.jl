```julia
function getdr(tm::AbstractTBModel, α::Int64, β::Int64, k::AbstractVector{<:Real})
-->dr::Matrix{ComplexF64}
```

$$
∂_β r_α
$$

を`tm`で`k`に対して計算します。r[n, m] = A[n, m] ただし n ≠ m の場合、r[n, n] = 0 です。

drは[Wang et al, 2019]の式(14)を直接微分することによって計算されます。dr[n, m]は、(i) バンドnとバンドmの両方が非縮退であるか、(ii) バンドnとバンドmの両方が完全に縮退しているが$E_n≠E_m$である場合にのみ正しいです。
