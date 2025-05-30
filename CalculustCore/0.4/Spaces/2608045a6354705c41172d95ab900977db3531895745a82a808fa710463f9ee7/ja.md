```julia
advectionOp(
    vels,
    V,
    discr;
    vel_update_funcs,
    vel_update_funcs!
)

```

移流演算子: (v⃗⋅∇)⋅  

v,u,T が H¹₀(Ω) の場合

(v,(u⃗⋅∇)T) = (v,ux*∂xT + uy*∂yT)

```
       = v' *B*(ux*∂xT + uy*∂yT)
```

実装としては

(u⃗⋅∇)T = ux*∂xT + uy*∂yT

```
   = [ux uy] * [Dx] T
               [Dx]
```
