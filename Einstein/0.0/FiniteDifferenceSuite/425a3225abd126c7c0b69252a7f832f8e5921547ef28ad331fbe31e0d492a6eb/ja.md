```
fdm_integrate_simpson(f::AbstractVector{T}, dx::T) where {T<:AbstractFloat}
```

グリッド間隔 `dx` を考慮して、シンプソンのルールを使用して関数 `f` を積分します。
