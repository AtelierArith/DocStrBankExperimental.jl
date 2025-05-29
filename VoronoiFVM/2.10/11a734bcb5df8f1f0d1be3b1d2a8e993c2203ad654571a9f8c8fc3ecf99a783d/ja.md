```julia
integrate(, coordl, coordr, hnormal, velofunc; kwargs...)

```

これは `integrate(::Type{<:Cartesian2D},...)` に似た内部関数ですが、代わりに $\int_{\sigma} r \, \mathbf{v} \cdot \mathbf{n} \,\mathrm{ds} \lvert x_K - x_L \rvert / \left ( \lvert\sigma\rvert r(\mathrm{mid}(\sigma)) \right )$ を計算します。ここで $r(\mathrm{mid}(\sigma))$ は $\sigma$ の中点の $r$-座標です。
