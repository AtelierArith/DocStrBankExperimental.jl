```
struct StandardRPSCrediting <: Crediting
```

Standard RPS crediting structure. Anything included in the RPS gentypes recieves a credit of 1.  Creates a [`CreditByGentype`](@ref)

`["solar", "dist_solar", "wind", "oswind", "geothermal", "hcc_new", "hcc_ret"]`
