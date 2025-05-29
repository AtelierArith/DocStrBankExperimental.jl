```
freqresp!(R::Array{T, 3}, sys::LTISystem, w_vec::AbstractVector{<:Real})
```

事前に割り当てられた配列 `R` のサイズ (ny, nu, nw)`を取る [`freqresp`](@ref) のインプレースバージョンです。
