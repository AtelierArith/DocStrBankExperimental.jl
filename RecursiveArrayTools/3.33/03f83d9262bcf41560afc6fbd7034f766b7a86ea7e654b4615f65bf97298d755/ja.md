```julia
recursive_unitless_bottom_eltype(a)
```

チェーンの底にある単位なし要素型を取得します。たとえば、onesが`Array{Array{Float64,N},N}`を持っている場合、これは`Float64`を返します。
