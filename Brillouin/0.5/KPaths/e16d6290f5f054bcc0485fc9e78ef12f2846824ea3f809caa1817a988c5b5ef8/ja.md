```
splice(kvs::AbstractVector{<:AbstractVector{<:Real}}, N::Integer)
                                                --> Vector{Vector{<:Real}}
```

離散的 **k**-点の間に補間された **k**-パスを返します。`kvs` の各隣接する **k**-点によって定義されるセグメントに `N` の補間点が挿入されます。

[`splice(::KPath, ::Integer)`](@ref) および [`interpolate`](@ref) も参照してください。

!!! warning "将来の非推奨"
    このメソッドシグネチャは、将来の Brillouin.jl のバージョンで非推奨になる可能性があります。

