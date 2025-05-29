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

v,u,T が H¹₀(Ω) において

(v,(u⃗⋅∇)T) = (v,ux*∂xT + uy*∂yT)

```
       = v' *B*(ux*∂xT + uy*∂yT)
```

として実装される

(u⃗⋅∇)T = ux*∂xT + uy*∂yT

```
   = [ux uy] * [Dx] T
               [Dx]
```
