```
pwaffine(m::JuMP.Model, x::Tuple, pwa::PWAFunc{C,D}; z=nothing, kwargs...) where {C,D}
```

JuMPモデル`m`に対して、JuMP変数`z`がJuMP変数`x`のピースワイズ線形関数/近似`pwa`であるという制約を追加します。
