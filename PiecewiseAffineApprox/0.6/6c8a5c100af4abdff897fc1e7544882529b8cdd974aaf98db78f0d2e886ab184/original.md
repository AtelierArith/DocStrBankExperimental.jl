```
pwaffine(m::JuMP.Model, x::Tuple, pwa::PWAFunc{C,D}; z=nothing, kwargs...) where {C,D}
```

Add constraints to JuMP-model `m` for JuMP-variable `z` as a   piecewise linear function/approximation `pwa` of JuMP-variables `x`    
