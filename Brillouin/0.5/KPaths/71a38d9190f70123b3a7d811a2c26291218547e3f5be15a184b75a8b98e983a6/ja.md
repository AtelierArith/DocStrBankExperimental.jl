```
interpolate(kvs::AbstractVector{<:AbstractVector{<:Real}}, N::Integer)
                                                --> Vector{Vector{<:Real}}
```

離散的 **k**-点の間に補間された **k**-パスを返します。`kvs` において、合計で約 `N` の補間点が得られます（通常はそれより少ない）。

一般的に、すべての補間された **k**-点が等間隔であるようにすることは不可能です。ただし、サンプルは `kvs` の点によって定義された各線分に沿って*正確に*等間隔であり、すべての線分にわたって*おおよそ*等間隔です。

[`interpolate(::KPath, ::Integer)`](@ref) および [`splice`](@ref) も参照してください。

!!! warning "将来の非推奨"
    このメソッドシグネチャは、将来の Brillouin.jl のバージョンで非推奨になる可能性があります。

