```julia
getA(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Real})
-->A::Matrix{ComplexF64}
```

バリー接続 $i⟨u_n|∂_α|u_m⟩$ を `tm` で `k` に対して計算します。

計算方法は [Wang et al, 2019] に提供されています。関連する方程式は式 (14) です。式 (14) はバンド m が非縮退であることを仮定しているため、A[n, m] は m が非縮退または完全に縮退している場合にのみ正しいです。
