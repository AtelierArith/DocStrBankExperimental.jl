```
LegendreWeight{T}()
LegendreWeight()
```

区間[-1,1]上のレジェンドル重み関数（定数1）を表す準ベクトル。[`legendreweight`](@ref)および[`Legendre`](@ref)も参照してください。

# 例

```jldoctest
julia> w = LegendreWeight()
LegendreWeight{Float64}()

julia> w[0.5]
1.0

julia> axes(w)
(Inclusion(-1.0 .. 1.0 (Chebyshev)),)
```
