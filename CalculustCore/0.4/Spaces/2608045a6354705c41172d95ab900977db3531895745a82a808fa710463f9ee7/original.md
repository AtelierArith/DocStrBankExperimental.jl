```julia
advectionOp(
    vels,
    V,
    discr;
    vel_update_funcs,
    vel_update_funcs!
)

```

Advection Operator: (v⃗⋅∇)⋅  

for v,u,T in H¹₀(Ω)

(v,(u⃗⋅∇)T) = (v,ux*∂xT + uy*∂yT)

```
       = v' *B*(ux*∂xT + uy*∂yT)
```

implemented as

(u⃗⋅∇)T = ux*∂xT + uy*∂yT

```
   = [ux uy] * [Dx] T
               [Dx]
```
