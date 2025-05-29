```
param_props(S,ξ₁,ξ₂,dξ₁,dξ₂;tangentplane=true) -> (x,n̂,dA,x₄)
```

Properties of a parametric surface function `x=S(ξ₁,ξ₂)`. Returns `x`, the  unit normal `n̂=n/|n|` and the surface area `dA≈|n|`, where `n≡T₁×T₂` and the  tangent vectors are `T₁=dξ₁*∂x/∂ξ₁` and `T₂=dξ₂*∂x/∂ξ₂`. x₄ are the 2x2  Gauss-point locations, optionally projected onto the `tangentplane`.
